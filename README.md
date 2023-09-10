[![icpp-llm](https://github.com/icppWorld/icpp-llm/actions/workflows/cicd.yml/badge.svg)](https://github.com/icppWorld/icpp-llm/actions/workflows/cicd.yml)

# LLMs for the Internet Computer

![icpp-llm logo](./assets/icpp-llm-logo.png)

Video: [How to run llama2.c on the Internet Computer](https://www.loom.com/share/a065b678df63462fb2f637d1b550b5d2?sid=1aeee693-25c0-4d1f-be0c-8231b53eb742)

# Connexus repository

Repository created for future implementations in the Connexus protocol. We want to combine the benefits of artificial intelligence to advise good investments according to the user's score.

# scripts made by the team translated into Portuguese:

```bash
git clone
https://github.com/icppWorld/icpp-llm/tree/main/icpp_llama2

```
```bash
cd icpp_llama2
```
```bash
pip install -r requirements.txt
```
```bash
icpp install-wasi-sdk
```
```bash
sh -ci "$(curl -fsSL https://internetcomputer.org/install.sh)"
```
```bash
dfx --version
```

- se nao funcionar: https://docs.icpp.world/installation.html

# on Linux/Mac
```bash
mkdir -p models
wget -P models https://huggingface.co/karpathy/tinyllamas/resolve/main/stories15M.bin
```

- criou a pasta e o modelo basico, na documentacao falam para instalar:
https://huggingface.co/karpathy/tinyllamas/tree/main/stories260K

em um terminal separado rodem a aplicacao:
```bash
dfx start --clean
```

- Olhem a pasta demo.sh para ver alguns comandos.

Em outro terminal execute:

```bash
python -m scripts.upload
```

- Deve aparecer a seguinte mensagem ao final:
Congratulations, your llama2 canister is ready for inference!
💯 🎉 🏁

Para testar execute:

```bash
dfx canister call llama2 inference '(record {prompt = "Afonso the man" : text; steps = 19 : nat64; temperature = 0.9 : float32; topp = 0.9 : float32; rng_seed = 0 : nat64;})'
```

# The Benefits of Running LLMs On-Chain

The canisters within the Internet Computer have certain constraints. They come with memory restrictions, and there's a cap on the number of instructions one can execute per message, as discussed [here](https://forum.dfinity.org/t/instruction-limit-is-crushing-me/22070/10?u=icpp).

This might lead one to question the rationale behind operating an LLM within an Internet Computer's canister.

For me, the primary incentive is the unparalleled simplicity of using the IC in comparison to conventional cloud platforms. You develop, deploy & test using a local replica of the cloud, and when everything is ready, you deploy it to the IC with just one command. Everything becomes instantly and securely accessible online. You can very easily restrict access to the endpoints in case you don't want to make it fully public yet and want to share it with a smaller group instead. 

Thanks to the Internet Computer's foundational cryptographic and blockchain technologies, concerns related to IT and security vanish. It's truly remarkable.

With such user-friendliness, the IC canister runtime serves as an ideal environment for my research pursuits. It complements the type of research presented in this paper that offers a dataset designed to boost the creation, examination, and study of Language Models for areas with scarce resources or specific niches:

 > [TinyStories: How Small Can Language Models Be and Still Speak
Coherent English?](https://arxiv.org/pdf/2305.07759.pdf)

Besides the ease of use and the enhanced security, running LLMs directly on-chain also facilitates a seamless integration of tokenomics, eliminating the need to juggle between a complex blend of web3 and web2 components, and I believe it will lead to a new category of Generative AI based dApps.

# Try it

`icpp_llama2` with the stories15M.bin is running on-chain in canister `4c4bn-daaaa-aaaag-abvcq-cai`. 

You can call it's inference endpoint with:

```bash
dfx canister call --network ic 4c4bn-daaaa-aaaag-abvcq-cai inference '(record {prompt = "" : text; steps = 20 : nat64; temperature = 0.8 : float32; topp = 1.0 : float32;})'
(
  variant {
    ok = "Once upon a time, there was a little boat named Bob. Bob loved to float on the water"
  },
)
```


## Instructions

See the README in the icpp_llama2 folder


## Support

For support, kindly create a GitHub Issue as outlined in the [Support](https://docs.icpp.world/support.html) documentation page.
  