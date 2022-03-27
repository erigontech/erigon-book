# Architecture of Erigon

Erigon is different from many other implementations of Ethereum (or other blockchain protocols) is that it is less monolithic and more modular. But the word "modular" here needs to be understood quite specifically. Modules are not just code packages that end up complied into a single executable. In Erigon, modules (or we more often call them "components") are parts of Erigon that can be taken out into a separate executable, and then operated in its own process (of the operating system), or even on its own computer in the network. Below is the illustration of how Erigon currently splits up into components (modules):

