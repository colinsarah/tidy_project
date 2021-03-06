# :rocket: This is Tidy Project

### 1. setuptools.setup参数含义

- name - 项目的名称
- version - 项目的版本。需要注意的是，PyPI上只允许一个版本存在，如果后续代码有了任何更改，再次上传需要增加版本号
- author和author_email - 项目作者的名字和邮件
- description - 项目的简短描述
- long_description - 项目的详细描述，会显示在PyPI的项目描述页面。上面的例子里直接用了README.md中的内容做详细描述
- long_description_content_type - 用于指定long_description的markup类型，上面的例子是markdown
- url - 项目主页的URL，一般给出代码仓库的链接
- packages - 指定最终发布的包中要包含的packages。上面的例子中find_packages() 会自动发现项目根目录下所有的packages，当然也可以手动指定package的名字
- install_requires - 项目依赖哪些库，这些库会在pip install的时候自动安装
- entry_points - 上面的例子中entry_points用来自动创建脚本，上面的例子在pip - install安装成功后会创建douyin_image这个命令，直接可以在命令行运行，很方便
- classifiers - 其他信息，一般包括项目支持的Python版本，License，支持的操作系统。上面的例子中，我们指定项目只能在Python 3上运行，使用MIT License，不依赖操作系统。关于classifiers的完整列表，可参考 https://pypi.org/classifiers/。

### 2. 打包项目

> pip install setuptools
> pip install wheel
> python setup.py sdist bdist_wheel

上面的命令会在dist/目录下生成一个tar.gz的源码包和一个.whl的Wheel包。

```shell

dist/
  douyin_image-0.1-py3-none-any.whl
  douyin_image-0.1.tar.gz
 ```

打包完之后，我们可以从本地安装库，来验证我们的项目能否被成功安装，如下

>pip3 install dist/douyin_image-0.1-py3-none-any.whl

### 3. 创建Pypi账户

- 上传项目到PyPI
- 我们使用twine上传项目，先安装twine
  
>pip3 install twine

安装完之后，运行下面的命令将库上传

>twine upload dist/*

上传完成后，我们的项目就成功地发布到PyPI了

>https://pypi.org/project/tidy-project/0.1/