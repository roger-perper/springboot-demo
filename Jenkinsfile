pipeline {


    agent none     //不指定Agent，后续每个Stage再指定
      stage ('Checkout Scm') {
        steps {
            script{
            	abortBuildTrigger()
            }
            checkout(scm)
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
}
