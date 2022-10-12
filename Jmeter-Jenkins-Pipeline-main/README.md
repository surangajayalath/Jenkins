# Jmeter-Jenkins-Pipeline
### Demostration video - https://drive.google.com/drive/folders/1e38v91ZTXdGo4aIAjiRYvEqmrQe6pJp3?usp=sharing
### This project related to https://github.com/surangajayalath/Jmeter-Jenkins-Intergration

### Prerequisites
* First complete above task(use link)
* Configure Performance Plugin in Jenkins

![Screenshot 2022-01-27 at 1 32 06 PM](https://user-images.githubusercontent.com/56903228/151316374-44c22cf0-5cd9-45a7-8ec6-3d60b3f91cc3.png)


* Pipeline Scrit(Scripted Pipeline)
```
node {
    stage("stage1") {
        //run shell  script in jmeter /bin folder
        sh '''#!/bin/bash
        cd /Users/suranga/Downloads/apache-jmeter-5.4.3/bin
        sh jmeter.sh -Jjmeter.save.saveservice.output_format=xml -n -t /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/Test_one.jmx -l /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/msjtest2.jtl
        '''
    }
    stage("copy file to jenkins") {
        // copy the file to jenkins early step we created
        sh 'cp /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/msjtest2.jtl  /Users/suranga/.jenkins/workspace/Jmeter+Pipeline'
    }
        stage("performance test") {
        //check performance
        performanceReport filterRegex: '', sourceDataFiles: 'msjtest2.jtl'
    }
}
```
![Screenshot 2022-01-27 at 1 26 24 PM](https://user-images.githubusercontent.com/56903228/151315423-57077cd8-537c-4ac8-a3a1-8d54953a0eee.png)

## Outputs

* Performance Trend

![Screenshot 2022-01-27 at 1 27 16 PM](https://user-images.githubusercontent.com/56903228/151315573-73effb05-3d85-4eb7-8ba5-c506146fca5c.png)

* Dashboard

![Screenshot 2022-01-27 at 1 28 14 PM](https://user-images.githubusercontent.com/56903228/151315799-ef404917-2e27-4340-8d28-237e856237b6.png)

* Console Output

![Screenshot 2022-01-27 at 1 28 49 PM](https://user-images.githubusercontent.com/56903228/151315874-d77059bc-7865-4311-89af-3e15bf82eed8.png)

