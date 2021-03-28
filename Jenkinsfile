pipeline {


    agent none     //不指定Agent，后续每个Stage再指定
    stages {
       stage('Preparation') {    //指定Stage名称Preparation
            agent { node { label 'master' } }    //指定Preparation的Stage执行的Agent为master(主节点)
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/$ver']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitlab', url: 'https://github.com/roger-perper/springboot-demo.git']]])   //Git的Checkout操作，拉去最新的代码
			   echo "代码检出完成"
            }
        }
        
        
		stage('Build') {      //指定Stage名称Build
            agent { node { label 'master' } }  //指定Preparation的Stage执行的Agent为master(主节点)
            steps {
                dir(env.WORKSPACE){   //指定后续Step的操作在Jenkins Workspace的目录下
                  sh "mvn clean install "   //Maven构建操作
                  junit allowEmptyResults: true, keepLongStdio: true, testResults: 'target/surefire-reports/*.xml'  //Junit插件收集单元测试结果
                 sh "mvn surefire-report:report"
                  sh "mv target/sample-0.0.1-SNAPSHOT.jar target/sample.jar"    //重命名文件
                 echo "打包jar完成"
                }
            }
        }
        

    }
}
