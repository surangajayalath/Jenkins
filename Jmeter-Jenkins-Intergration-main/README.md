# Jmeter-Jenkins-Intergration(http request)
* Simulation Video - https://drive.google.com/drive/folders/1e38v91ZTXdGo4aIAjiRYvEqmrQe6pJp3?usp=sharing

## Step 1 → Install Jenkins
## Step 2 → Get jenkins performance plugins
## Step 3 → Go to Jemeter/bin
* Vim user.properties → add line
```
jmeter.save.saveservice.output_format=xml 
```

![Screenshot 2022-01-11 at 11 44 42 AM](https://user-images.githubusercontent.com/56903228/148890882-5f328355-8b6a-4ef2-84cd-1e7d3cf36108.png)

* Step 4 → Create a Jmeter test

![Screenshot 2022-01-11 at 11 45 14 AM](https://user-images.githubusercontent.com/56903228/148890940-0d31f5e6-b28b-429b-844a-2f3aeec8b842.png)

* Step 5 → Run Jmeter test from command line
```
cd /Users/suranga/Downloads/apache-jmeter-5.4.3/bin

sh jmeter.sh -Jjmeter.save.saveservice.output_format=xml -n -t /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/Test_Plan.jmx -l /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/msjtest.jtl
```
![Screenshot 2022-01-11 at 11 48 03 AM](https://user-images.githubusercontent.com/56903228/148891241-4d2acdf2-8890-49ed-8874-cad085f56f55.png)

## Step 6 → Add a job in jenkins, add jmeter commands in build step(freestyle)
## Step 7 → Add post build action, publish performance test reports

![Screenshot 2022-01-11 at 11 41 44 AM](https://user-images.githubusercontent.com/56903228/148890598-492038f3-78c2-4c16-9e3d-b5daa14da6b8.png)

```
cd /Users/suranga/Downloads/apache-jmeter-5.4.3/bin

sh jmeter.sh -Jjmeter.save.saveservice.output_format=xml -n -t /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/Test_Plan.jmx -l /Users/suranga/Downloads/apache-jmeter-5.4.3/bin/msjtest.jtl
```
### Explain
* -n —> non gui
* -t —> for give the location test file
* -l —> location of result file
* add saved file path

![Screenshot 2022-01-11 at 11 42 19 AM](https://user-images.githubusercontent.com/56903228/148890653-dad01431-34c6-4aa7-870d-7379e570aa2f.png)

## Build and see outputs
![Screenshot 2022-01-11 at 11 50 07 AM](https://user-images.githubusercontent.com/56903228/148891459-27bed66c-c8ca-4f56-aaf9-959eb49b44f3.png)

* if build many time you can see different behaviors of graphs

![Screenshot 2022-01-11 at 11 49 39 AM](https://user-images.githubusercontent.com/56903228/148891408-5f2de623-0752-47f7-a649-613141f0e6ff.png)


