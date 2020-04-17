# 在Windows上安装PyTorch
可以在各种Windows发行版上安装和使用PyTorch。根据您的系统和计算要求，您在Windows上使用PyTorch的经验可能会在处理时间方面有所不同。为了充分利用PyTorch的<a href="https://developer.nvidia.com/cuda-zone" target="_blank">CUDA</a><a href="https://pytorch.org/tutorials/beginner/blitz/tensor_tutorial.html?highlight=cuda#cuda-tensors" target="_blank">支持</a>的能力，建议您的Windows系统具有NVIDIA GPU。
## 先决条件
### 支持的Windows发行版
以下的Windows发行版支持PyTorch：
- <a href="https://www.microsoft.com/en-us/windows" target="_blank">Windows</a> 7及更高版本；建议使用<a href="https://www.microsoft.com/en-us/software-download/windows10ISO" target="_blank">Windows 10</a>或更高版本。
- <a href="https://docs.microsoft.com/en-us/windows-server/windows-server" target="_blank">Windows Server 2008 R2</a>及更高版本
<table><tr><td bgcolor=#CCCCCC> 此处安装说明通常适用于所有受支持的Windows发行版。显示特定示例将在Windows 10企业版计算机中运行。 </td></tr></table> 

### Python
目前，Windows上的PyTorch仅支持Python3.x，不支持Python2.x。
Windows在默认情况下没有安装Python，您可以通过如下多种方法进行安装：

- [Chocolatey](https://chocolatey.org/)
- [Python website](https://www.python.org/downloads/windows/)
- [Anaconda](https://pytorch.org/get-started/locally/#anaconda)


<table><tr><td bgcolor=#CCCCCC> 如果您使用Anaconda安装Python，同时将安装sandboxed版本的Python用于运行PyTorch应用。 </td></tr></table>

<table><tr><td bgcolor=#CCCCCC> 如果您决定使用Chocolatey安装Python但还没有安装Chocolatey，请确保您正在<a href="https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/" target="_blank">以管理员的身份运行命令提示符。 </td></tr></table>

通过Chocolatey成功安装Python后，<a href="https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/" target="_blank">以管理员的身份在命令提示符</a>中运行以下命令：

<table><tr><td bgcolor=#EAEAEA> choco install python </td></tr></table>

## 软件包管理器
安装PyTorch二进制文件，您需要安装至少<a href="https://www.anaconda.com/download/#windows" target="_blank">Anaconda</a>或<a href="https://pypi.org/project/pip/" target="_blank">pip</a>中的任意一种软件包管理器。我们推荐您使用Anaconda，因为它将在一个sandboxed安装中为您提供所有PyTorch依赖项，包括Python和pip。

### Anaconda
安装Anaconda，您需要使用PyTorch 3.x的<a href="https://www.anaconda.com/download/#windows" target="_blank">64位图形安装程序</a>。单击安装程序链接后选择“Run”，Anaconda将完成下载并显示安装提示。使用默认选项即可。

### pip
如果您已通过上述推荐的任何一种方法安装Python，<a href="https://pypi.org/project/pip/" target="_blank">pip</a>则已为您安装成功。

## 安装
### Anaconda
通过Anaconda安装PyTorch，你需要运行如下命令打开Anaconda命令提示符：
<table><tr><td bgcolor=#EAEAEA> Start | Anaconda3| Anaconda Prompt </td></tr></table>

#### 无CUDA
通过Anaconda安装PyTorch且没有支持CUDA的系统或不需要CUDA，请在<a href="https://pytorch.org/get-started/locally/#windows-package-manager">官网的选择器</a>中选择操作系统：Windows，安装包：Conda，CUDA：None。选择完成后，运行选择器中提供的命令。

#### 有CUDA
通过Anaconda安装PyTorch且具备支持CUDA的系统，在<a href="https://pytorch.org/get-started/locally/#windows-package-manager">官网的选择器</a>中选择系统：Windows，安装包：Conda，CUDA版本根据您当前计算机支持的版本进行选择。通常情况下，我们建议使用最新的CUDA版本。选择完成后，运行选择器中提供的命令。

### pip

#### 无CUDA
通过pip安装PyTorch且没有支持CUDA的系统或不需要CUDA，请在<a href="https://pytorch.org/get-started/locally/#windows-package-manager">官网的选择器</a>中选择操作系统：Windows，安装包：Pip，CUDA：None。选择完成后，运行选择器中提供的命令。

#### 有CUDA
通过pip安装PyTorch且具备支持CUDA的系统，请在<a href="https://pytorch.org/get-started/locally/#windows-package-manager">官网的选择器</a>中选择操作系统：Windows，安装包：Pip，CUDA版本根据您当前计算机支持的版本进行选择。通常情况下，我们建议使用最新的CUDA版本。选择完成后，运行选择器中提供的命令。

## 验证
为了确保PyTorch已正确安装，我们将通过运行PyTorch代码样例进行验证。在这里，我们将构造一个随机初始化的张量。
在命令行中，输入：
<table><tr><td bgcolor=#EAEAEA> python </td></tr></table>

然后输入以下代码：
<table><tr><td bgcolor=#EAEAEA> 

**from** __future__ **import** print_function

**import** torch

x = torch.rand(5, 3)

**print**(x) 
</td></tr></table>

输出应类似于以下内容：

<table><tr><td bgcolor=#EAEAEA> 
"tensor([
         
         [0.3380, 0.3845, 0.3217],
         [0.8337, 0.9050, 0.2650],
         [0.2979, 0.7141, 0.9069],
         [0.1449, 0.1132, 0.1375],
         [0.4675, 0.3947, 0.1426]
])
</td></tr></table>

此外，要检查PyTorch是否启用了GPU驱动程序,和检查CUDA可以通过其访问，请运行以下命令以返回是否启用了CUDA驱动程序：
<table><tr><td bgcolor=#EAEAEA> 

**import** torch

torch.cuda.is_available()

</td></tr></table>

## 从源构建

对于大多数PyTorch用户，通过软件包管理器从预编译的二进制文件进行安装将提供最佳体验。但是，有时无论是为了在PyTorch内核上进行测试还是实际开发，您可能都想要安装的PyTorch代码。想要安装最新的PyTorch代码，您将需要<a href="https://github.com/pytorch/pytorch#from-source">从源构建PyTorch</a>。
### 先决条件
1. 安装<a href="https://pytorch.org/get-started/locally/#anaconda">Anaconda</a>。
2. 如果您的计算机具备<a href="https://developer.nvidia.com/cuda-gpus">支持CUDA的GPU</a>，安装<a href="https://developer.nvidia.com/cuda-downloads">CUDA</a>。
3. 如果您想要在Windows操作系统上构建，您还需要安装Visual Studio 2017 14.11工具集和NVTX。需要特别注意的是，在Windows上构建CUDA 8，对VS 2015 Update 3及其相应的补丁有额外的要求。补丁的详细信息可以在<a href="https://support.microsoft.com/en-gb/help/4020481/fix-link-exe-crashes-with-a-fatal-lnk1000-error-when-you-use-wholearch">这里</a>找到。
4. 请按照链接中描述的步骤进行操作：https://github.com/pytorch/pytorch#from-source。

您可以根据<a href="https://pytorch.org/get-started/locally/#windows-verification">如上所述</a>验证安装是否成功。