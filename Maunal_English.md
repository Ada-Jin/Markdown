# Installing on Windows


PyTorch can be installed and used on various Windows distributions. Depending on your system and compute requirements, your experience with PyTorch on Windows may vary in terms of processing time. It is recommended, but not required, that your Windows system has an NVIDIA GPU in order to harness the full power of PyTorch’s <a href="https://developer.nvidia.com/cuda-zone" target="_blank">CUDA</a><a href="https://pytorch.org/tutorials/beginner/blitz/tensor_tutorial.html?highlight=cuda#cuda-tensors" target="_blank"> support</a>.


## PREREQUISITES
### Supported Windows Distributions
PyTorch is supported on the following Windows distributions:
- <a href="https://www.microsoft.com/en-us/windows" target="_blank">Windows</a> 7and greater; <a href="https://www.microsoft.com/en-us/software-download/windows10ISO" target="_blank">Windows 10</a> or greater recommended
- <a href="https://docs.microsoft.com/en-us/windows-server/windows-server" target="_blank">Windows Server 2008 R2</a>and greater
<table><tr><td bgcolor=#CCCCCC> The install instructions here will generally apply to all supported Windows distributions. The specific examples shown will be run on a Windows 10 Enterprise machine. </td></tr></table> 

### Python
Currently, PyTorch on Windows only supports Python 3.x; Python 2.x is not supported.

As it is not installed by default on Windows, there are multiple ways to install Python:

- [Chocolatey](https://chocolatey.org/)
- [Python website](https://www.python.org/downloads/windows/)
- [Anaconda](https://pytorch.org/get-started/locally/#anaconda)


<table><tr><td bgcolor=#CCCCCC> If you use Anaconda to install PyTorch, it will install a sandboxed version of Python that will be used for running PyTorch applications. </td></tr></table>

<table><tr><td bgcolor=#CCCCCC> If you decide to use Chocolatey, and haven’t installed Chocolatey yet, ensure that you are<a href="https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/" target="_blank"> running your command prompt as an administrator. </td></tr></table>

For a Chocolatey-based install, run the following command in an <a href="https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/" target="_blank">administrative command prompt</a>：

<table><tr><td bgcolor=#EAEAEA> choco install python </td></tr></table>

## Package Manager
To install the PyTorch binaries, you will need to use at least one of two supported package managers:<a href="https://www.anaconda.com/download/#windows" target="_blank"> Anaconda</a> and <a href="https://pypi.org/project/pip/" target="_blank">pip</a>. Anaconda is the recommended package manager as it will provide you all of the PyTorch dependencies in one, sandboxed install, including Python and pip.

### Anaconda
To install Anaconda, you will use the <a href="https://www.anaconda.com/download/#windows" target="_blank">64-bit graphical installer</a> for PyTorch 3.x. Click on the installer link and select “Run”. Anaconda will download and the installer prompt will be presented to you. The default options are generally sane.

### pip
If you installed Python by any of the recommended ways above[LINK], <a href="https://pypi.org/project/pip/" target="_blank">pip</a> will have already been installed for you.

## INSTALLATION
### Anaconda
To install PyTorch with Anaconda, you will need to open an Anaconda prompt via <table><tr><td bgcolor=#EAEAEA> Start | Anaconda3| Anaconda Prompt </td></tr></table>

#### No CUDA
To install PyTorch via Anaconda, and do not have a <a href="https://developer.nvidia.com/cuda-zone">CUDA-capable</a> system or do not require CUDA, in the <a href="https://pytorch.org/get-started/locally/#windows-package-manager">selector in website</a>, choose OS: Windows, Package: Conda and CUDA: None. Then, run the command that is presented to you.

#### With CUDA
To install PyTorch via Anaconda, and you do have a <a href="https://developer.nvidia.com/cuda-zone">CUDA-capable</a> system, in the <a href="https://pytorch.org/get-started/locally/#windows-package-manager">selector in website</a>, choose OS: Windows, Package: Conda and the CUDA version suited to your machine. Often, the latest CUDA version is better. Then, run the command that is presented to you.

### pip

#### No CUDA
To install PyTorch via pip, and do not have a <a href="https://developer.nvidia.com/cuda-zone">CUDA-capable</a> system or do not require CUDA, in the <a href="https://pytorch.org/get-started/locally/#windows-package-manager">selector in website</a>, choose OS: Windows, Package: Pip and CUDA: None. Then, run the command that is presented to you.

#### WithCUDA
To install PyTorch via pip, and do have a <a href="https://developer.nvidia.com/cuda-zone">CUDA-capable</a> system, in the <a href="https://pytorch.org/get-started/locally/#windows-package-manager">selector in website</a>, choose OS: Windows, Package: Pip and the CUDA version suited to your machine. Often, the latest CUDA version is better. Then, run the command that is presented to you.

## VERIFICATION
To ensure that PyTorch was installed correctly, we can verify the installation by running sample PyTorch code. Here we will construct a randomly initialized tensor.

From the command line, type:
<table><tr><td bgcolor=#EAEAEA> python </td></tr></table>

then enter the following code:
<table><tr><td bgcolor=#EAEAEA> 

**from** __future__ **import** print_function

**import** torch

x = torch.rand(5, 3)

**print**(x) 
</td></tr></table>

The output should be something similar to:

<table><tr><td bgcolor=#EAEAEA> 
"tensor([
         
         [0.3380, 0.3845, 0.3217],
         [0.8337, 0.9050, 0.2650],
         [0.2979, 0.7141, 0.9069],
         [0.1449, 0.1132, 0.1375],
         [0.4675, 0.3947, 0.1426]
])
</td></tr></table>

Additionally, to check if your GPU driver and CUDA is enabled and accessible by PyTorch, run the following commands to return whether or not the CUDA driver is enabled:
<table><tr><td bgcolor=#EAEAEA> 

**import** torch

torch.cuda.is_available()

</td></tr></table>

## BUILDING FROM SOURCE

For the majority of PyTorch users, installing from a pre-built binary via a package manager will provide the best experience. However, there are times when you may want to install the bleeding edge PyTorch code, whether for testing or actual development on the PyTorch core. To install the latest PyTorch code, you will need to <a href="https://github.com/pytorch/pytorch#from-source">build PyTorch from source</a>。
### Prerequisites
1. Install <a href="https://pytorch.org/get-started/locally/#anaconda">Anaconda</a>.
2. Install <a href="https://developer.nvidia.com/cuda-downloads">CUDA</a>, if your machine has a <a href="https://developer.nvidia.com/cuda-gpus">CUDA-dnabled GPU</a>.
3. If you want to build on Windows, Visual Studio 2017 14.11 toolset and NVTX are also needed. Especially, for CUDA 8 build on Windows, there will be an additional requirement for VS 2015 Update 3 and a patch for it. The details of the patch can be found out <a href="https://support.microsoft.com/en-gb/help/4020481/fix-link-exe-crashes-with-a-fatal-lnk1000-error-when-you-use-wholearch">here</a>.
4. Follow the steps described here: https://github.com/pytorch/pytorch#from-source.

You can verify the installation as described <a href="https://pytorch.org/get-started/locally/#windows-verification">here</a>.