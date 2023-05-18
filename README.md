
hello 
cl100k_base = tiktoken.get_encoding("cl100k_base")

# In production, load the arguments directly instead of accessing private attributes
# See openai_public.py for examples of arguments for specific encodings
enc = tiktoken.Encoding(
    # If you're changing the set of special tokens, make sure to use a different name
    # It should be clear from the name what behaviour to expect.
    name="cl100k_im",
    pat_str=cl100k_base._pat_str,
    mergeable_ranks=cl100k_base._mergeable_ranks,
    special_tokens={
        **cl100k_base._special_tokens,
        "<|im_start|>": 100264,
        "<|im_end|>": 100265,
    }
)
   my_tiktoken_extension
├── tiktoken_ext
│   └── my_encodings.py
└── setup.py


from setuptools import setup, find_namespace_packages

setup(
    name="my_tiktoken_extension",
    packages=find_namespace_packages(include=['tiktoken_ext*']),
    install_requires=["tiktoken"],
    ...
)

   
