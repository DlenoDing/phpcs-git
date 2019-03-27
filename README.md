1.把路径D:\myFiles\Php-Cs\php72n加入到PATH中

2.用git命令下载（或直接下载）仓库源码，然后直接执行：
git clone https://github.com/squizlabs/PHP_CodeSniffer.git

cd D:\myFiles\Php-Cs\PHPCodeSniffer

php bin/phpcs -h

php bin/phpcbf -h


3.在Windows系统中，实际是执行phpcs.bat文件，这个文件又引用了同目录下的phpcs文件。

在phpcs.bat中，我们需要配置两个变量，才能在CMD中正确执行phpcs命令。

如下，需指定php.exe和phpcs文件的绝对位置：

if "%PHPBIN%" == "" set PHPBIN=D:\myFiles\Php-Cs\php72n\php.exe

if not exist "%PHPBIN%" if "%PHP_PEAR_PHP_BIN%" neq "" goto USE_PEAR_PATH

GOTO RUN

:USE_PEAR_PATH

set PHPBIN=%PHP_PEAR_PHP_BIN%

:RUN

"%PHPBIN%" "%~dp0\phpcs" %*

4.把路径D:\myFiles\Php-Cs\PHPCodeSniffer\bin加入到PATH中，就可以在CMD中执行phpcs了。
说明：phpcbf也需要这样的修改。

5.将./gitHook/pre-commit覆盖到项目.git\hooks下

6.设置到编辑器phpStrom
