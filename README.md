# nf-ipfs
description copied from issue #1

## New feature
### Motivation
Decentralized storage and direct content addressing of scientific data are central element of the decentralized science agenda, a movement that combines open science ideas with new web3 tools. The ability to pin data via [IPFS](https://ipfs.io/) has improved in the last months. With the introduction of [estuary](https://estuary.tech/), scientific data can be published to IPFS at a very low cost without centralized control by, for example, a cloud service provider.  

### Feature description
A minimal plugin which allows the following operations of increasing complexity and dependency (thank you Rob Syme for breaking them down nicely): 

1) Pulling input data from IPFS (as if it were coming from HTTPS or FTP) - currently implemented `openlab file pull`
2) Enabling "upload" of final output datasets to IPFS - currently implemented `openlab file push`
3) Encoding the dependency graph of all intermediate steps at the end of the workflow for maximum reproducibility. This can be done by uploading the work directories (with or without the intermediate data files), logfiles, and configs.  

#### configuration and dependencies
using the plugin will require installation of the openlab CLI which currently supports: 
1) pulling input data from ipfs - `openlab file pull`
2) uploading input data to ipfs using estuary - `openlab file push`

the openlab CLI will allow users to add thei API keys for services like estuary. Currently, LabDAO creates temporary API keys for all users to store their data publicly in a shared pool.

#### paths 
files will be addressable using their ipfs URI - an example: 
`ipfs://QmSMDgLrWbPax4ibxky6LapitrCpwGfSizmSYQuw1hrnuH`

## Usage scenario 
* a sample list is passed to nf-core RNA-Seq and fastq files are downloaded from IPFS before processing starts
* the result of the RNA-Seq application run is deposited on IPFS together with intermediary files, logs (and configs)

```
plugins {
    id 'nf-ipfs'
}
```
## Related code
https://github.com/labdao/openlab-cli

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Anybody working on an IPFS plugin for <a href="https://twitter.com/nextflowio?ref_src=twsrc%5Etfw">@nextflowio</a>? At <a href="https://twitter.com/lab_dao?ref_src=twsrc%5Etfw">@lab_dao</a> we are planning to build this plugin for decentralized scientific compute - please DM if interested in joining <a href="https://twitter.com/blahah404?ref_src=twsrc%5Etfw">@blahah404</a>, me and team🌱🧬 (cc <a href="https://twitter.com/robsyme?ref_src=twsrc%5Etfw">@robsyme</a>)</p>&mdash; Niklas Rindtorff (@Niklas_TR) <a href="https://twitter.com/Niklas_TR/status/1504461873714016263?ref_src=twsrc%5Etfw">March 17, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
