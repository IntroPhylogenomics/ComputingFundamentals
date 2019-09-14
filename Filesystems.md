# Navigating Filesystems

## Filesystem Structure

The base of the filesystem in Unix-based operating systems (like Linux and Mac OS, which we will focus on exclusively in this workshop) is indicated with a single forward slash (`/`) and is known as the root. All files and folders are stored somewhere with a path (i.e., address) that starts at the root. Folders are hierarchical, so paths to highly nested folders will need to include all parent folders.
  
![ExampleMacFilesystem](https://github.com/IntroPhylogenomics/ComputingFundamentals/blob/master/filesystem.png)
  
## Absolute v Relative Paths
  
- [ ] Absolute paths
	- All absolute paths begin at the root- start with /
- [ ] Relative paths
	- dont start with /
	- Working directories
	- Shortcuts for current and parent directories
- [ ] Hidden files and folders
	- Names begin with `.`
	- Usually used for configuration files
