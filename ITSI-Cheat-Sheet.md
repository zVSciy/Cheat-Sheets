# ITSI Cheat sheet

## Tools 
- Memory Dumping - [FTK Imager](https://accessdata.com/product-download/ftk-imager-version-4-2-0)
- Memory Analysis - [Volatility2](https://github.com/volatilityfoundation/volatility)
- Memory Analysis - [Volatility3](https://github.com/volatilityfoundation/volatility3)

## Volatility2
depending on the install, you may need to run `volatility` instead of `vol.py`
### Get Image Info
`vol.py -f cridex.vmem imageinfo`
### Get Process List
`vol.py -f cridex.vmem --profile=WinXPSP3x86 pslist`
### Get Full Process List With Hidden Processes
`$ vol.py -f cridex.vmem --profile=WinXPSP2x86 psxview`
### View Network Connections
`vol.py -f  [vmem_file] -profile WinXPSP2x86 netscan`
### Find malware in deirectory
`vol.py -f  [vmem_file] -profile WinXPSP2x86 malfind -D [directory]`
### List All DLL's
`vol.py -f  [vmem_file] -profile WinXPSP2x86 dlllist`
### Export Dll's Of A Process
`$ vol.py -f cridex.vmem --profile=WinXPSP2x86 --pid=584 dlldump -D /tmp `
