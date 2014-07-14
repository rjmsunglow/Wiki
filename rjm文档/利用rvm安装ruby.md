安装rvm
\curl -sSL https://get.rvm.io | bash -s stable

rvm安装ruby
rvm install ruby-1.9.2-p320

如果出现 缺少 Xcodeproj。0.6.0 的错误：
rvm reinstall ruby-2.0.0-p247 --with-gcc=clang --verify-downloads 1

命令：
./bin/submodules
pod install