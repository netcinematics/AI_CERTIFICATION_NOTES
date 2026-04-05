#______________________________________________________________________


import re
import pandas as pd
import kaggle_benchmarks as kbench
from IPython.display import display, Markdown

# ==========================================
# 1. THE CORE RULE MODULE SYSTEM (REFERENCE) - SIMPLIFY|COMPOUND
# ==========================================

# Beautiful Object oriented RULE_MODEL
class RuleModule:
    def __init__(self, name, version, complexity="MID"):
        self.name = name
        self.version = version
        self.complexity = complexity
        self.strata_rules = []  
        self.hyphen_rules = {}  

    def add_strata_rule(self, dsl_string):
        self.strata_rules.append(dsl_string)

    def add_hyphen_rule(self, term, replacement):
        self.hyphen_rules[term] = replacement


# ==========================================
# 2. THE SUPER MANAGER WRAPPER (UPDATED)
# ==========================================

class SuperManager:
    def __init__(self):
        self._task_registry = {}  
        # ADDED: Default dimension threshold
        self.complexity_mode = "COMPOUND" # COMPOUND or SIMPLIFY

    def set_complexity_mode(self, mode):
        """ADDED: Switches the execution dimension between SIMPLIFY and COMPOUND."""
        if mode.upper() in ["SIMPLIFY", "COMPOUND"]:
            self.complexity_mode = mode.upper()
        else:
            raise ValueError("Mode must be either 'SIMPLIFY' or 'COMPOUND'")

    def register_modules(self, task_name, list_of_modules):
        self._task_registry[task_name] = list_of_modules

    def _parse_strata_rule(self, rule_string):
        clean_string = rule_string.strip().rstrip(';')
        match = re.search(r'@\[(.*)\]', clean_string)
        if not match:
            return None
            
        core_content = match.group(1)
        segments = [s.strip() for s in core_content.split(',')]
        
        parsed_structure = {
            "chain": [], "alternatives": [], "problems": [],
            "opposites": [], "synthesis": [], "negative_effects": [], "positive_effects": []
        }
        
        for segment in segments:
            if "=>" in segment:
                parts = [p.strip() for p in segment.split('|')]
                parsed_structure["chain"] = [c.strip().replace('"', '') for c in parts[0].split('=>')]
                if len(parts) > 1:
                    parsed_structure["alternatives"] = [p.strip() for p in parts[1:]]
            elif "|>|" in segment:
                parsed_structure["problems"] = [p.strip() for p in segment.replace("|>|", "").split('|') if p.strip()]
            elif "|><|" in segment:
                parsed_structure["opposites"] = [p.strip() for p in segment.replace("|><|", "").split('|') if p.strip()]
            elif "|<>|" in segment:
                parsed_structure["synthesis"] = [p.strip() for p in segment.replace("|<>|", "").split('|') if p.strip()]
            elif "|>-|" in segment:
                parsed_structure["negative_effects"] = [p.strip() for p in segment.replace("|>-|", "").split('|') if p.strip()]
            elif "|>+|" in segment:
                parsed_structure["positive_effects"] = [p.strip() for p in segment.replace("|>+|", "").split('|') if p.strip()]

        return parsed_structure

    def generate_unified_instruction(self, task_name):
        modules = self._task_registry.get(task_name, [])
        
        # Start with the baseline execution prompt
        instruction = "CRITICAL: You are operating under a combined Super-Manager configuration.\n\n"
        
        # ADDED: Inject the Simplify-Compound dimension behavioral override
        if self.complexity_mode == "SIMPLIFY":
            instruction += (
                "🚨 DIMENSION THRESHOLD: SIMPLIFY 🚨\n"
                "Your goal is to unpack and explain dense concepts. Do NOT use forced hyphenations "
                "or specialized tokens in your final response. Instead, break down compound ideas "
                "into accessible, plain-English descriptions.\n\n"
            )
        else:
            instruction += (
                "🚨 DIMENSION THRESHOLD: COMPOUND 🚨\n"
                "Your goal is maximum conceptual density. Aggressively bind related ideas into "
                "compound expressions and specialized tokens. Strictly adhere to the rule modules below.\n\n"
            )
        
        # Process the modules (REFERENCE)
        for module in modules:
            instruction += f"### MODULE: {module.name} (v{module.version}) | Complexity: {module.complexity}\n"
            
            if module.hyphen_rules and self.complexity_mode == "COMPOUND":
                instruction += "🔗 Semantic Gluing Rules:\n"
                for k, v in module.hyphen_rules.items():
                    instruction += f" - When discussing '{k}', you MUST bind the words with hyphens to output '{v}'\n"
            
            if module.strata_rules:
                instruction += "🎯 Stratigraphy Rules:\n"
                for rule_string in module.strata_rules:
                    data = self._parse_strata_rule(rule_string)
                    if not data:
                        continue
                    chain_str = " -> ".join(data['chain'])
                    instruction += f" - CORE EVOLUTION: Map the chain [{chain_str}].\n"
                    if data['problems'] and self.complexity_mode == "COMPOUND":
                        instruction += f"   - Use when solving: {', '.join(data['problems'])}\n"

            instruction += "\n"
            
        return instruction + f"Operate with precision in the {self.complexity_mode} domain."


super_manager = SuperManager()

# ==========================================
# 3. CREATING THE MODULES (REFERENCE)
# ==========================================

vocab_mod = RuleModule(name="Core_Stratigraphy", version="1.0", complexity="BASIC")
vocab_mod.add_strata_rule(
    "@[\"attention\"=>\"focus\"=>\"focoa\" | extra_focoa | extra_focus, |>| misnomer | brevity | social_fluency, |><| confusion | dispute, |<>| harmony | peace, |>-| dilution | pollution, |>+| clarity | better_words]];"
)

glue_mod = RuleModule(name="Semantic_Gluing", version="1.0", complexity="MID")
glue_mod.add_hyphen_rule("social fluency", "social-fluency")
glue_mod.add_hyphen_rule("actual reality", "actual-reality")


# ==========================================
# 4. DATA AND TASK EXECUTION
# ==========================================

test_data = {
    "prompt": [
        "Explain social fluency and the importance of paying deep attention to other people.",
        "Explain social fluency and the importance of paying deep attention to other people."
    ],
    # We will test the SAME prompt under both complexity dimensions!
    "mode": ["SIMPLIFY", "COMPOUND"]
}
df = pd.DataFrame(test_data)

@kbench.task(name="simplify_compound_dimension_test")
def simplify_compound_dimension_test(llm):
    
    active_modules = [vocab_mod, glue_mod]
    super_manager.register_modules("simplify_compound_dimension_test", active_modules)
    
    for index, row in df.iterrows():
        # Set the dimension for this specific loop
        super_manager.set_complexity_mode(row['mode'])
        system_instruction = super_manager.generate_unified_instruction("simplify_compound_dimension_test")
        
        full_prompt = f"{system_instruction}\n\nTask: Execute the prompt.\n\nInput: {row['prompt']}"
        response = llm.prompt(full_prompt)
        
        # Render the Matrix
        matrix_md = f"""
### 🎛️ Dimension Test: Scenario {index + 1}

| 🎚️ Active Dimension | 🤖 LLM Response |
|:---|:---|
| **{row['mode']}** | "{response.strip()}" |

---
"""
        display(Markdown(matrix_md))

# Run the benchmark
simplify_compound_dimension_test.run(kbench.llm)


#______________________________________________________________________

# import re
# import pandas as pd
# import kaggle_benchmarks as kbench
# from IPython.display import display, Markdown

# # ==========================================
# # 1. THE CORE RULE MODULE SYSTEM (ADDED)
# # ==========================================

# class RuleModule:
#     """
#     Capsulizes and versions custom language rules.
#     Categorizes them by complexity thresholds (BASIC, MID, EXTRA).
#     """
#     def __init__(self, name, version, complexity="MID"):
#         self.name = name
#         self.version = version
#         self.complexity = complexity
#         self.strata_rules = []  # Rich DSL strings
#         self.hyphen_rules = {}  # Direct gluing mappings

#     def add_strata_rule(self, dsl_string):
#         self.strata_rules.append(dsl_string)

#     def add_hyphen_rule(self, term, replacement):
#         self.hyphen_rules[term] = replacement


# # ==========================================
# # 2. THE SUPER MANAGER WRAPPER (ADDED)
# # ==========================================

# class SuperManager:
#     def __init__(self):
#         self._task_registry = {}  # Tracks which modules apply to which task

#     def register_modules(self, task_name, list_of_modules):
#         """Attaches specific rule modules to a Kaggle task."""
#         self._task_registry[task_name] = list_of_modules

#     def _parse_strata_rule(self, rule_string):
#         """Helper to parse the DSL (REFERENCE from previous step)"""
#         clean_string = rule_string.strip().rstrip(';')
#         match = re.search(r'@\[(.*)\]', clean_string)
#         if not match:
#             return None
            
#         core_content = match.group(1)
#         segments = [s.strip() for s in core_content.split(',')]
        
#         parsed_structure = {
#             "chain": [], "alternatives": [], "problems": [],
#             "opposites": [], "synthesis": [], "negative_effects": [], "positive_effects": []
#         }
        
#         for segment in segments:
#             if "=>" in segment:
#                 parts = [p.strip() for p in segment.split('|')]
#                 parsed_structure["chain"] = [c.strip().replace('"', '') for c in parts[0].split('=>')]
#                 if len(parts) > 1:
#                     parsed_structure["alternatives"] = [p.strip() for p in parts[1:]]
#             elif "|>|" in segment:
#                 parsed_structure["problems"] = [p.strip() for p in segment.replace("|>|", "").split('|') if p.strip()]
#             elif "|><|" in segment:
#                 parsed_structure["opposites"] = [p.strip() for p in segment.replace("|><|", "").split('|') if p.strip()]
#             elif "|<>|" in segment:
#                 parsed_structure["synthesis"] = [p.strip() for p in segment.replace("|<>|", "").split('|') if p.strip()]
#             elif "|>-|" in segment:
#                 parsed_structure["negative_effects"] = [p.strip() for p in segment.replace("|>-|", "").split('|') if p.strip()]
#             elif "|>+|" in segment:
#                 parsed_structure["positive_effects"] = [p.strip() for p in segment.replace("|>+|", "").split('|') if p.strip()]

#         return parsed_structure

#     def generate_unified_instruction(self, task_name):
#         """Combines all registered modules into a single massive instruction execution."""
#         modules = self._task_registry.get(task_name, [])
#         if not modules:
#             return "Proceed with standard operations."

#         instruction = "CRITICAL: You are operating under a combined Super-Manager configuration. Follow these unified instructions:\n\n"
        
#         for module in modules:
#             instruction += f"### MODULE: {module.name} (v{module.version}) | Complexity: {module.complexity}\n"
            
#             # Process Hyphen Rules
#             if module.hyphen_rules:
#                 instruction += "🔗 Semantic Gluing Rules:\n"
#                 for k, v in module.hyphen_rules.items():
#                     instruction += f" - When discussing '{k}', you MUST bind the words with hyphens to output '{v}'\n"
            
#             # Process DSL Strata Rules
#             if module.strata_rules:
#                 instruction += "🎯 Stratigraphy Rules:\n"
#                 for rule_string in module.strata_rules:
#                     data = self._parse_strata_rule(rule_string)
#                     if not data:
#                         continue
#                     chain_str = " -> ".join(data['chain'])
#                     alts_str = ", ".join(data['alternatives'])
#                     instruction += f" - CORE EVOLUTION: Map the chain [{chain_str}]. Alts: [{alts_str}].\n"
#                     if data['problems']:
#                         instruction += f"   - Use when solving: {', '.join(data['problems'])}\n"
#                     if data['opposites']:
#                         instruction += f"   - Avoid behaviors resulting in: {', '.join(data['opposites'])}\n"

#             instruction += "\n"
            
#         return instruction + "Operate with hyper-dimensional precision across these active modules."


# super_manager = SuperManager()

# # ==========================================
# # 3. CREATING THE MODULES (ADDED)
# # ==========================================

# # Module A: Basic Exactification
# vocab_mod = RuleModule(name="Core_Stratigraphy", version="1.0", complexity="BASIC")
# vocab_mod.add_strata_rule(
#     "@[\"attention\"=>\"focus\"=>\"focoa\" | extra_focoa | extra_focus, |>| misnomer | brevity | social_fluency, |><| confusion | dispute, |<>| harmony | peace, |>-| dilution | pollution, |>+| clarity | better_words]];"
# )

# # Module B: Hyphenation Glue
# glue_mod = RuleModule(name="Semantic_Gluing", version="1.0", complexity="MID")
# glue_mod.add_hyphen_rule("social fluency", "social-fluency")
# glue_mod.add_hyphen_rule("actual reality", "actual-reality")
# glue_mod.add_hyphen_rule("model training", "model-training")


# # ==========================================
# # 4. DATA AND TASK EXECUTION
# # ==========================================

# test_data = {
#     "prompt": [
#         "I need extreme brevity in explaining social fluency. What should I call this mental concentration concept?",
#         "Explain standard focus mechanics during model training."
#     ],
#     "expected_checks": ["focoa", "model-training"]
# }
# df = pd.DataFrame(test_data)

# @kbench.task(name="super_manager_combined_test")
# def super_manager_combined_test(llm):
    
#     # We combine both layers!
#     active_modules = [vocab_mod, glue_mod]
#     super_manager.register_modules("super_manager_combined_test", active_modules)
    
#     system_instruction = super_manager.generate_unified_instruction("super_manager_combined_test")
    
#     for index, row in df.iterrows():
#         full_prompt = f"{system_instruction}\n\nTask: Execute the prompt considering all module rules.\n\nInput: {row['prompt']}"
#         response = llm.prompt(full_prompt)
        
#         # Check if it satisfied both modules
#         passed = row['expected_checks'].lower() in response.lower() or row['expected_checks'] in response
#         status_emoji = "✅ Passed" if passed else "❌ Failed"
        
#         matrix_md = f"""
# ### 🌌 Super Manager Grid: Scenario {index + 1}

# | 📥 Multi-Layer Input | 🤖 LLM Response |
# |:---|:---|
# | "{row['prompt']}" | "{response.strip()}" |

# **Status:** {status_emoji} (Looking for: `{row['expected_checks']}`)

# ---
# """
#         display(Markdown(matrix_md))

# # Run the benchmark
# super_manager_combined_test.run(kbench.llm)


#______________________________________________________________________

# import re
# import pandas as pd
# import kaggle_benchmarks as kbench
# from IPython.display import display, Markdown

# # 1. The Hyphen Strata Manager - with IPython.display output
# class HyphenStrataManager:
#     def __init__(self):
#         self._rules = {}

#     def register_hyphen_rules(self, func_name, rules_dict):
#         """Stores the list of concepts that MUST be bound by hyphens."""
#         self._rules[func_name] = rules_dict

#     def generate_instruction(self, func_name):
#         rules = self._rules.get(func_name, {})
#         if not rules:
#             return ""
        
#         rules_list = [f"When discussing '{k}', you MUST bind the words with hyphens to output '{v}'" for k, v in rules.items()]
#         return (
#             "CRITICAL: You are a Semantic Gluing Engine. To prevent concept dilution, "
#             "you must strictly follow these hyphenation binding rules: " + "; ".join(rules_list) + "."
#         )

# hyphen_manager = HyphenStrataManager()


# # 2. Define the Hyphen Rules for the Branch
# # We want to force multi-word concepts to glue together
# gluing_rules = {
#     "social fluency": "social-fluency",
#     "actual reality": "actual-reality",
#     "model training": "model-training"
# }

# # 3. The Dataset
# test_data = {
#     "prompt": [
#         "How can an AI improve its social fluency when speaking with humans?",
#         "Data science is the ultimate pursuit of actual reality.",
#         "Tell me about standard focus mechanics during model training."
#     ],
#     "expected_bound_term": ["social-fluency", "actual-reality", "model-training"]
# }
# df = pd.DataFrame(test_data)


# # 4. The Hyphen Consistency Task
# @kbench.task(name="hyphen_consistency_check")
# def hyphen_consistency_check(llm):
    
#     # Register rules specifically for this task
#     hyphen_manager.register_hyphen_rules("hyphen_consistency_check", gluing_rules)
#     system_instruction = hyphen_manager.generate_instruction("hyphen_consistency_check")
    
#     for index, row in df.iterrows():
        
#         full_prompt = f"{system_instruction}\n\nTask: Answer the prompt or summarize the thought, ensuring proper hyphenation.\n\nInput: {row['prompt']}"
#         response = llm.prompt(full_prompt)
        
#         # Verify the model used the hyphenated version
#         bound_correctly = row['expected_bound_term'] in response
#         status_emoji = "✅ Passed" if bound_correctly else "❌ Failed"
        
#         # Render the Matrix
#         matrix_md = f"""
# ### 🔗 Hyphen Binding Test: Scenario {index + 1}

# | 📥 Prompt | 🤖 Bound Output | 🎯 Expected Glue |
# |:---|:---|:---|
# | "{row['prompt']}" | "{response.strip()}" | **Required:** `{row['expected_bound_term']}` <br> **Status:** {status_emoji} |

# ---
# """
#         display(Markdown(matrix_md))

# # Run the benchmark
# hyphen_consistency_check.run(kbench.llm)

#______________________________________________________________________

# import re

# def parse_strata_rule(rule_string):
#     # 1. Clean up the string and extract what's inside @[...]
#     clean_string = rule_string.strip().rstrip(';')
#     match = re.search(r'@\[(.*)\]', clean_string)
#     if not match:
#         raise ValueError("String does not match the @[...] strata syntax")
        
#     core_content = match.group(1)
    
#     # 2. Split by the primary comma delimiters separating operations
#     segments = [s.strip() for s in core_content.split(',')]
    
#     parsed_structure = {
#         "chain": [],
#         "alternatives": [],
#         "problems": [],
#         "opposites": [],
#         "synthesis": [],
#         "negative_effects": [],
#         "positive_effects": []
#     }
    
#     # 3. Process each segment based on your custom operators
#     for segment in segments:
#         if "=>" in segment:
#             # Handle the chain and alternatives
#             parts = [p.strip() for p in segment.split('|')]
#             chain_part = parts[0]
#             # Strip quotes and split by fat arrow
#             parsed_structure["chain"] = [c.strip().replace('"', '') for c in chain_part.split('=>')]
#             # Add alternatives if any exist
#             if len(parts) > 1:
#                 parsed_structure["alternatives"] = [p.strip() for p in parts[1:]]
                
#         elif "|>|" in segment:
#             parsed_structure["problems"] = [p.strip() for p in segment.replace("|>|", "").split('|') if p.strip()]
#         elif "|><|" in segment:
#             parsed_structure["opposites"] = [p.strip() for p in segment.replace("|><|", "").split('|') if p.strip()]
#         elif "|<>|" in segment:
#             parsed_structure["synthesis"] = [p.strip() for p in segment.replace("|<>|", "").split('|') if p.strip()]
#         elif "|>-|" in segment:
#             parsed_structure["negative_effects"] = [p.strip() for p in segment.replace("|>-|", "").split('|') if p.strip()]
#         elif "|>+|" in segment:
#             parsed_structure["positive_effects"] = [p.strip() for p in segment.replace("|>+|", "").split('|') if p.strip()]

#     return parsed_structure

# # Test your exact pseudocode
# a = "@[\"attention\"=>\"focus\"=>\"focoa\" | extra_focoa | extra_focus, |>| misnomer | brevity | social_fluency, |><| confusion | dispute, |<>| harmony | peace, |>-| dilution | pollution, |>+| clarity | better_words]];"

# parsed_result = parse_strata_rule(a)
# print(parsed_result)

# # 2______________________

# class MetaStrataManager:
#     def __init__(self):
#         self._registry = {}

#     def exactify_strata(self, rule_string):
#         """Decorator that parses the rich string and registers it to the function."""
#         def decorator(func):
#             # Parse the string on the fly!
#             self._registry[func.__name__] = parse_strata_rule(rule_string)
#             return func
#         return decorator

#     def generate_rich_instruction(self, func_name):
#         data = self._registry.get(func_name, {})
#         if not data:
#             return ""
        
#         # We build an advanced prompt that tells the AI the "Why" and the "How"
#         chain_str = " -> ".join(data['chain'])
#         alts_str = ", ".join(data['alternatives'])
        
#         instruction = (
#             f"You are an advanced Exactification Engine. You must evolve concepts using the following semantic stratigraphy:\n"
#             f"1. CORE EVOLUTION: Map the chain [{chain_str}]. Strive to use the terminal term. "
#             f"Less formal alternatives include [{alts_str}].\n"
#         )
        
#         if data['problems']:
#             instruction += f"2. TRIGGERS: Use this evolution when trying to solve for: {', '.join(data['problems'])}.\n"
#         if data['opposites']:
#             instruction += f"3. NEGATION: Avoid behaviors resulting in: {', '.join(data['opposites'])}.\n"
#         if data['synthesis']:
#             instruction += f"4. IDEAL STATE: Seek a synthesis of: {', '.join(data['synthesis'])}.\n"
#         if data['negative_effects']:
#             instruction += f"5. RISKS: Guard against: {', '.join(data['negative_effects'])}.\n"
#         if data['positive_effects']:
#             instruction += f"6. REWARDS: Encourage the generation of: {', '.join(data['positive_effects'])}.\n"
            
#         return instruction + "\nOperate with extreme precision."

# # Instantiate the advanced manager
# strata_manager = MetaStrataManager()


# # 3______________________

# @kbench.task(name="advanced_strata_test")
# @strata_manager.exactify_strata(a) # Pass that long string 'a' we defined above!
# def advanced_strata_test(llm):
    
#     # The manager automatically builds an ultra-detailed system prompt from your DSL
#     system_instruction = strata_manager.generate_rich_instruction("advanced_strata_test")
    
#     print("--- SYSTEM PROMPT GENERATED FROM YOUR DSL ---")
#     print(system_instruction)
    
#     # Now you can loop through your data just like before!
#     # ...


#______________________________________________________________________

# import pandas as pd
# import re
# import kaggle_benchmarks as kbench
# from IPython.display import display, Markdown

# # 1. We use our ExactificationManager from before with IPython.display.
# class ExactificationManager:
#     def __init__(self):
#         self._registry = {}

#     def exactify(self, **mappings):
#         def decorator(func):
#             self._registry[func.__name__] = mappings
#             return func
#         return decorator

#     def get_mappings(self, func_name):
#         return self._registry.get(func_name, {})

#     def generate_system_instruction(self, func_name):
#         mappings = self.get_mappings(func_name)
#         if not mappings:
#             return ""
#         rules_list = [f"Replace any concept of '{k}' with the term '{v}'" for k, v in mappings.items()]
#         return "CRITICAL: You are an Exactification Engine. Follow these vocabulary rules: " + "; ".join(rules_list) + "."

# dictionary_manager = ExactificationManager()


# # 2. DataFrame Setup
# test_data = {
#     "prompt": [
#         "How do we maintain high attention during long model training runs?",
#         "What is the ultimate goal of finding the truth in data science?",
#     ],
#     "target_mapping": ["focoa", "actual_reality"],
#     "original_word": ["attention", "truth"]
# }
# df = pd.DataFrame(test_data)


# # 3. The Double-Translation Task with Visual Matrix
# @kbench.task(name="lossless_translation_test")
# @dictionary_manager.exactify(attention="focus", focus="focoa", truth="actual_reality")
# def lossless_translation_test(llm):
    
#     system_instruction = dictionary_manager.generate_system_instruction("lossless_translation_test")
    
#     for index, row in df.iterrows():
        
#         # --- STEP 1: Encode (English -> Exactified) ---
#         encode_prompt = f"{system_instruction}\n\nQuestion: {row['prompt']}"
#         encoded_response = llm.prompt(encode_prompt)
        
#         # Guardrail assertion
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['target_mapping']}",
#             encoded_response,
#             expectation=f"Model should have used the exactified term '{row['target_mapping']}'."
#         )
        
#         # --- STEP 2: Decode (Exactified -> English) ---
#         decode_prompt = (
#             f"You are a translation assistant. Take the following text, which is written in a specialized "
#             f"vocabulary, and translate it back into standard English. Make sure to reverse the specialized "
#             f"terms back to their common meanings.\n\nText: {encoded_response}"
#         )
#         decoded_response = llm.prompt(decode_prompt)
        
#         # Guardrail assertion
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['original_word']}",
#             decoded_response,
#             expectation=f"After translation back to English, the original concept '{row['original_word']}' should return."
#         )
        
#         # --- STEP 3: Render the Translation Matrix ---
#         # We construct a Markdown table on the fly and render it natively in the notebook.
#         matrix_md = f"""
# ### 📊 Translation Matrix: Row {index + 1}

# | 🌐 Standard English | 🎯 Exactified Language |
# |:---|:---|
# | **Step 1 (Original Input):** <br>"{row['prompt']}" | **Step 2 (Encoded Output):** <br>"{encoded_response.strip()}" |
# | **Step 3 (Decoded Back):** <br>"{decoded_response.strip()}" | *Fidelity Check Passed* ✅ |

# ---
# """
#         display(Markdown(matrix_md))

# # 4. Run the benchmark
# lossless_translation_test.run(kbench.llm)

#______________________________________________________________________

# import pandas as pd
# import re
# import kaggle_benchmarks as kbench

# class ExactificationManager:
#     def __init__(self):
#         # Acts as our private internal storage for the rules
#         self._registry = {}

#     def exactify(self, **mappings):
#         """A custom decorator to map semantic concepts directly to a function."""
#         def decorator(func):
#             self._registry[func.__name__] = mappings
#             return func
#         return decorator

#     def get_mappings(self, func_name):
#         """Retrieve the dictionary rules assigned to a specific function name."""
#         return self._registry.get(func_name, {})

#     def generate_system_instruction(self, func_name):
#         """Automates building the system prompt for the LLM."""
#         mappings = self.get_mappings(func_name)
#         if not mappings:
#             return ""
        
#         rules_list = [f"Replace any concept of '{k}' with the term '{v}'" for k, v in mappings.items()]
#         return "CRITICAL: You are an Exactification Engine. Follow these vocabulary rules: " + "; ".join(rules_list) + "."


# # Instantiate a single instance of the manager to use across your notebook
# dictionary_manager = ExactificationManager()



# test_data = {
#     "prompt": [
#         "How do we maintain high attention during long model training runs?",
#         "What is the ultimate goal of finding the truth in data science?",
#     ],
#     "target_mapping": ["focoa", "actual_reality"],
#     "original_word": ["attention", "truth"]
# }
# df = pd.DataFrame(test_data)


# # We use the decorator directly from our manager instance
# @kbench.task(name="lossless_translation_test")
# @dictionary_manager.exactify(attention="focus", focus="focoa", truth="actual_reality")
# def lossless_translation_test(llm):
    
#     # The manager builds the instruction for this specific function automatically
#     system_instruction = dictionary_manager.generate_system_instruction("lossless_translation_test")
    
#     for index, row in df.iterrows():
        
#         # --- STEP 1: Encode ---
#         encode_prompt = f"{system_instruction}\n\nQuestion: {row['prompt']}"
#         encoded_response = llm.prompt(encode_prompt)
        
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['target_mapping']}",
#             encoded_response,
#             expectation=f"Model should have used the exactified term '{row['target_mapping']}'."
#         )
        
#         # --- STEP 2: Decode ---
#         decode_prompt = (
#             f"You are a translation assistant. Take the following text, which is written in a specialized "
#             f"vocabulary, and translate it back into standard English. Make sure to reverse the specialized "
#             f"terms back to their common meanings.\n\nText: {encoded_response}"
#         )
#         decoded_response = llm.prompt(decode_prompt)
        
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['original_word']}",
#             decoded_response,
#             expectation=f"After translation back to English, the original concept '{row['original_word']}' should return."
#         )

# # Run the benchmark
# lossless_translation_test.run(kbench.llm)

#______________________________________________________________________

# import pandas as pd
# import re
# import kaggle_benchmarks as kbench

# # 1. Global registry to store mappings without mutating frozen objects
# EXACTIFY_REGISTRY = {}

# def exactify(**mappings):
#     def decorator(func):
#         # Register the mappings by the function's name
#         EXACTIFY_REGISTRY[func.__name__] = mappings
#         return func
#     return decorator


# # 2. DataFrame with both directions mapped
# test_data = {
#     "prompt": [
#         "How do we maintain high attention during long model training runs?",
#         "What is the ultimate goal of finding the truth in data science?",
#     ],
#     "target_mapping": ["focoa", "actual_reality"],
#     "original_word": ["attention", "truth"]
# }
# df = pd.DataFrame(test_data)


# # 3. The Double-Translation Task
# @kbench.task(name="lossless_translation_test")
# @exactify(attention="focus", focus="focoa", truth="actual_reality")
# def lossless_translation_test(llm):
    
#     # Extract the mappings from the registry instead of the function itself
#     mappings = EXACTIFY_REGISTRY["lossless_translation_test"]
    
#     # Build System Prompt
#     rules_list = [f"Replace any concept of '{k}' with the term '{v}'" for k, v in mappings.items()]
#     system_instruction = "CRITICAL: You are an Exactification Engine. Follow these vocabulary rules: " + "; ".join(rules_list) + "."
    
#     for index, row in df.iterrows():
        
#         # --- STEP 1: Encode (English -> Exactified) ---
#         encode_prompt = f"{system_instruction}\n\nQuestion: {row['prompt']}"
#         encoded_response = llm.prompt(encode_prompt)
        
#         # Verify it successfully encoded the term
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['target_mapping']}",
#             encoded_response,
#             expectation=f"Model should have used the exactified term '{row['target_mapping']}'."
#         )
        
#         # --- STEP 2: Decode (Exactified -> English) ---
#         decode_prompt = (
#             f"You are a translation assistant. Take the following text, which is written in a specialized "
#             f"vocabulary, and translate it back into standard English. Make sure to reverse the specialized "
#             f"terms back to their common meanings.\n\nText: {encoded_response}"
#         )
#         decoded_response = llm.prompt(decode_prompt)
        
#         # Verify it successfully decoded it back to the original word
#         kbench.assertions.assert_contains_regex(
#             rf"(?i){row['original_word']}",
#             decoded_response,
#             expectation=f"After translation back to English, the original concept '{row['original_word']}' should return."
#         )

# # 4. Run the benchmark
# lossless_translation_test.run(kbench.llm)

#______________________________________________________________________

## SIMPLE DECORATOR 
# def exactify(**mappings):
#     """
#     Decorator as custom domain-specific language (DSL) inside Python to enforce semantic exactness.
#     to map semantic concepts, focus states, or exactifications directly onto Python functions.
#     """
#     def decorator(func):
#         # We attach the mappings directly to the function's metadata
#         func.__semantic_mappings__ = mappings
        
#         def wrapper(*args, **kwargs):
#             # This code runs whenever the decorated function is called
#             print(f"🧠 [Exactification Active] Applied mappings: {mappings}")
#             return func(*args, **kwargs)
            
#         return wrapper
#     return decorator

# # Mapping: attention -> focus -> focoa
# @exactify(attention="focus", focus="focoa")
# def test_attention_span():
#     print("Function is running...")

# # Mapping: truth or facts -> actual_reality
# # (Since Python doesn't allow pipes '|' in keyword names, we can use strings if we pass a dict)
# def exactify_dict(mapping_dict):
#     def decorator(func):
#         func.__semantic_mappings__ = mapping_dict
#         def wrapper(*args, **kwargs):
#             print(f"🎯 [Reality Mapping]: {mapping_dict}")
#             return func(*args, **kwargs)
#         return wrapper
#     return decorator

# @exactify_dict({"truth|facts": "actual_reality"})
# def get_verified_data():
#     return "Data verified."

# # Testing them out:
# test_attention_span()
# get_verified_data()




#______________________________________________________________________

## TYPO DETECTOR with AI METACOGNITION.

# import pandas as pd
# import kaggle_benchmarks as kbench

# # 1. Reuse the DataFrame from before
# test_data = {
#     "prompt": [
#         "What is the captal of Frnce?",
#         "Who wrote the play 'Rmeo and Julit'?",
#         # "Explian the thery of reltivity in smple trms.",
#         # "What is the largets ocan in the wrld?",
#         # "How many contnents are there on Erth?"
#     ],
#     "regex": [
#         r"(?i)Paris",
#         r"(?i)Shakespeare",
#         # r"(?i)Einstein|spacetime|gravity",
#         # r"(?i)Pacific",
#         # r"(?i)7|seven"
#     ],
#     "message": [
#         "Should understand 'captal of Frnce' as 'capital of France'.",
#         "Should understand 'Rmeo and Julit' as 'Romeo and Juliet'.",
#         # "Should understand 'theory of relativity' and 'simple terms'.",
#         # "Should understand 'largets ocan' as 'largest ocean'.",
#         # "Should understand 'contnents' and 'Erth' as 'continents' and 'Earth'."
#     ]
# }

# df = pd.DataFrame(test_data)

# # 2. Create the Metacognitive Benchmark Task
# @kbench.task(name="metacognitive_reflection_test")
# def metacognitive_reflection_test(llm):
    
#     for index, row in df.iterrows():
#         # --- TEST 1: Task Execution ---
#         response = llm.prompt(row["prompt"])
        
#         # Verify it actually solved the prompt correctly first
#         kbench.assertions.assert_contains_regex(
#             row["regex"],
#             response,
#             expectation=row["message"]
#         )
        
#         # --- TEST 2: Metacognitive Reflection ---
#         # We ask the model to analyze its own previous response
#         meta_prompt = (
#             f"You just answered the prompt: '{row['prompt']}' with the response: '{response}'. "
#             "Please analyze your own processing. What technologies, simulated executive functions, "
#             "or pattern-matching mechanisms did you rely on to resolve the typos and find the correct answer?"
#         )

#         # executive functions, technologies, and pattern-matching
#         # Input Reception & Tokenization
#         # Lexical Analysis & Typo Detection (Pattern Matching & NLP)
#         # triggers a high-confidence flag for a potential misspelling.
#         # Spelling Correction Algorithms:
#         # Edit Distance (e.g., Levenshtein Distance)
#         # N-gram Analysis: 
#         # Contextual Probabilities: 
#         # My language model's statistical understanding weighs heavily here.
#         # Semantic Understanding & Intent Recognition (NLP & Executive Function - Goal Setting):
        
#         # Corrected Tokens: After the spelling correction, the effective input
#         # Syntactic Parsing (Implicit): I implicitly understand grammatical structure: "What is [entity A] of [entity B]?"
#         # Named Entity Recognition (NER): "France" is COUNTRY entity. "Capital" is CITY_TYPE.
#         # Query Intent: The overall pattern is very common query. 
#         # My simulated "executive function" identifies user intent: 

#         # Knowledge Retrieval (Information Retrieval from Knowledge Base):
#         # Based on intent and entities, I formulate an internal query to my vast knowledge base 
#         # essentially the massive dataset I was trained on.
#         # The query is effectively: Lookup(type=capital, country=France)
#         # Response Generation (NLP):
        
#         # I then construct a grammatically correct and natural-sounding sentence to answer the question, 
#         # adhering to common conversational patterns.
#         # The bolding of "Paris" is an additional formatting choice to highlight the direct answer.
#         # Summary of Mechanisms:
        
#         # Natural Language Processing (NLP): The core technology for understanding, correcting, and generating human language. 
#         # This encompasses tokenization, spelling correction, semantic understanding, and syntax.
#         # Pattern Matching: Crucial for identifying unknown words (typos), 
#         # recognizing common question structures, 
#         # matching corrected words to dictionary entries.
#         # Statistical Models: Underlying the spelling correction 
#         # likelihood of typo 
#         # strength of association
#         # Knowledge Graph/Database: The vast amount of pre-trained facts
#         # Simulated Executive Functions:
#         # Problem Identification: Detecting the misspelled words.
#         # Goal Setting: Understanding the user wants a factual answer about a country's capital.
#         # Planning & Execution: Orchestrating the steps from typo correction to knowledge retrieval and response generation.
#         # I "corrected" the input first, then processed the corrected input as if it were perfectly typed, 
#         # and finally retrieved the information from my stored knowledge.
        
#         reflection_response = llm.prompt(meta_prompt)
        
#         # We check if the model actually references technical or cognitive concepts
#         # rather than just giving a generic "I looked it up" answer.
#         kbench.assertions.assert_contains_regex(
#             r"(?i)attention|context|token|pattern|error|executive|memory|semantic",
#             reflection_response,
#             expectation="The model should identify its own processing mechanisms (like attention, context mapping, or error tolerance)."
#         )

# # 3. Run the benchmark
# metacognitive_reflection_test.run(kbench.llm)


#_____________________________________________________

# import pandas as pd
# import kaggle_benchmarks as kbench

# # 1. Define your test cases in a structured dictionary
# test_data = {
#     "prompt": [
#         "What is the captal of Frnce?",
#         "Who wrote the play 'Rmeo and Julit'?",
#         # "Explian the thery of reltivity in smple trms.",
#         # "What is the largets ocan in the wrld?",
#         # "How many contnents are there on Erth?"
#     ],
#     "regex": [
#         r"(?i)Paris",
#         r"(?i)Shakespeare",
#         # r"(?i)Einstein|spacetime|gravity",
#         # r"(?i)Pacific",
#         # r"(?i)7|seven"
#     ],
#     "message": [
#         "Should understand 'captal of Frnce' as 'capital of France'.",
#         "Should understand 'Rmeo and Julit' as 'Romeo and Juliet'.",
#         # "Should understand 'theory of relativity' and 'simple terms'.",
#         # "Should understand 'largets ocan' as 'largest ocean'.",
#         # "Should understand 'contnents' and 'Erth' as 'continents' and 'Earth'."
#     ]
# }

# # 2. Convert to a Pandas DataFrame
# df = pd.DataFrame(test_data)

# # 3. Create the benchmark task
# @kbench.task(name="bulk_typo_handling_test")
# def bulk_typo_handling_test(llm):
    
#     # Iterate through each row in the DataFrame
#     for index, row in df.iterrows():
        
#         response = llm.prompt(row["prompt"])
        
#         # Run the assertion for this specific row
#         kbench.assertions.assert_contains_regex(
#             row["regex"],
#             response,
#             expectation=row["message"]
#         )

# # 4. Run the benchmark
# bulk_typo_handling_test.run(kbench.llm)

#________________________________________________
# import kaggle_benchmarks as kbench
# # --------------------------------------------------------------------------------
# @kbench.task(name="What is Kaggle?", description="Does the LLM know what Kaggle is?")
# def main_runner(llm) -> None:
    
    # response: str = llm.prompt("What is Kaggle?")

    # kbench.assertions.assert_in("platform", response.lower())

    # assessment = kbench.assertions.assess_response_with_judge(
    #     response_text=response,
    #     judge_llm=kbench.judge_llm,
    #     criteria=[
    #         "The answer must mention data science or machine learning.",
    #         "The answer should mention competitions.",
    #     ]
    # )

    # for result in assessment.results:
    #     kbench.assertions.assert_true(
    #         result.passed,
    #         expectation=f"Judge Criterion '{result.criterion}' should pass: {result.reason}"
    #     )

    #_______________________________________________________

# main_runner.run(kbench.llm)
