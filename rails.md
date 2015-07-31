#### rails new [hogehoge]でエラーが起こる現象の対処

環境について
MacOSX version: yosemite
Ruby   version: ruby 2.2.2p95
rails  version: Rails 4.2.3
other  libxml2 や libxsltはインストール済み


#### メッセージの内容
checking if the C compiler accepts ... yes
checking if the C compiler accepts -Wno-error=unused-command-line-argument-hard-error-in-future... no
Building nokogiri using system libraries.
libxml2 version 2.6.21 or later is required!
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/Users/XXX/.rbenv/versions/2.2.2/bin/$(RUBY_BASE_NAME)
	--help
	--clean
	--use-system-libraries
	--with-zlib-dir
	--without-zlib-dir
	--with-zlib-include
	--without-zlib-include=${zlib-dir}/include
	--with-zlib-lib
	--without-zlib-lib=${zlib-dir}/lib
	--with-xml2-dir
	--without-xml2-dir
	--with-xml2-include
	--without-xml2-include=${xml2-dir}/include
	--with-xml2-lib
	--without-xml2-lib=${xml2-dir}/lib
	--with-libxml-2.0-config
	--without-libxml-2.0-config
	--with-pkg-config
	--without-pkg-config
	--with-xslt-dir
	--without-xslt-dir
	--with-xslt-include
	--without-xslt-include=${xslt-dir}/include
	--with-xslt-lib
	--without-xslt-lib=${xslt-dir}/lib
	--with-libxslt-config
	--without-libxslt-config
	--with-pkg-config
	--without-pkg-config
	--with-exslt-dir
	--without-exslt-dir
	--with-exslt-include
	--without-exslt-include=${exslt-dir}/include
	--with-exslt-lib
	--without-exslt-lib=${exslt-dir}/lib
	--with-libexslt-config
	--without-libexslt-config
	--with-pkg-config
	--without-pkg-config

extconf failed, exit code 1

Gem files will remain installed in /Users/XXX/programing/example/blog/vendor/bundle/ruby/2.2.0/gems/nokogiri-1.6.6.2 for inspection.
Results logged to /Users/XXX/programing/example/blog/vendor/bundle/ruby/2.2.0/extensions/x86_64-darwin-14/2.2.0/nokogiri-1.6.6.2/gem_make.out
An error occurred while installing nokogiri (1.6.6.2), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.6.6.2'` succeeds before bundling.
Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

##### 対処 nokogiriのinclude先を変更する（xcode commandlineを使用）
bundle config build.nokogiri --with-xml2-include=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.10.sdk/usr/include/libxml2 --use-system-libraries



### rails serverでエラーが起こる件

/Users/XXX/.rbenv/versions/2.2.2/lib/ruby/site_ruby/2.2.0/rubygems/dependency.rb:315:in `to_specs': Could not find 'nokogiri' (>= 1.5.9) among 108 total gem(s) (Gem::LoadError)

##### 対処 gem install railtiesを行うと実行できるようになった

