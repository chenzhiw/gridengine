compile & install on ubuntu 16.04.3
#1. Compile#

I. Download jdk, [javacc](https://javacc.org/downloads/javacc-6.0.zip "javacc"), [apache ant](http://www-us.apache.org/dist/ant/binaries/apache-ant-1.10.1-bin.tar.gz "apache ant") and [junit package](http://repo1.maven.org/maven2/org/junit/ "junit package").


II. Edit **build.properties** file:

 - javacc.home=*your_javacc_path*
 - libs.junit.classpath=*your_junit_file_path*

III. configure the environment and compile

    export SGE_ROOT=/usr/local/gridengine
    export JAVA_HOME=*your_java_home_path*
    export JRE_HOME=$JAVA_HOME/jre
    export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
    export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib
    
    cd source
    sudo apt-get install gcc make csh libhwloc-dev libpam0g-dev libxext-dev libncurses-dev libssl-dev libdb-dev libmotif-dev
    
    ./aimk -only-depend
    ./scripts/zerodepend
    ./aimk depend
    ./aimk
	

#2. Install#
    sudo -E ./inst_sge -m -x -auto inst_template.conf
