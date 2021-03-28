pipeline {

    stages {
       stage('Preparation') {    //指定Stage名称Preparation
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/roger-perper/springboot-demo.git']]])   //Git的Checkout操作，拉去最新的代码
			   echo "代码检出完成"
            }
        }
        
        
		stage('Build') {      //指定Stage名称Build
            steps {
                  sh "mvn clean install "   //Maven构建操作
                  sh "mv target/sample-0.0.1-SNAPSHOT.jar target/sample.jar"    //重命名文件
                 echo "打包jar完成"
                }
            }
        }
        

    }
