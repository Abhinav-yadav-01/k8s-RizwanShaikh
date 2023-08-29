# Basics of yaml

## 01: Comments & Key Value Pairs
- Space after colon is mandatory to differentiate key and value
```yml
# Defining simple key value pairs
name: rizwan
age: 25
city: Pune
```

## 02: Dictionary / Map
- Equal amount of blank space required for all the items under a dictionary
```yml
person:
  name: rizwan
  age: 25
  city: Pune
```

## Step-03: Array / Lists
- Dash indicates an element of an array
```yml
person: # Dictionary
  name: rizwan
  age: 25
  city: pune
  hobbies: # List  
    - riding
    - swimming
  hobbies: [riding, swimming]   # List with a differnt notation  
```  

## Step-04: Multiple Lists
- Dash indicates an element of an array
```yml
person: # Dictionary
  name: rizwan
  age: 25
  city: pune
  hobbies: # List  
    - riding
    - swimming
  hobbies: [riding, swimming]   # List with a differnt notation  
  friends: # 
    - name: friend1
      age: 22
    - name: friend2
      age: 25            
```  


## Sample Pod Template for Reference

```yml
apiVersion: v1 # String
kind: Pod # String
metadata: # Dictionary
  name: demo-pod
  labels: # Dictionary
    app: demoApp
spec: # Dictionary
  containers: # List
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```        

## Sample ReplicaSet Template for Reference

```yml
apiVersion: v1
kind: ReplicaSet
metadata:
  name: demo-rs
spec:
  replicas: 2
  selector:
    matchLabels:
      app: demoApp
  template:
    metadata: # Dictionary
      name: demo-pod
      labels: # Dictionary
        app: demoApp
    spec: # Dictionary
      containers: # List
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
```            

## Sample Deployment Template for Reference

```yml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deploy
spec: 
  replicas: 3
  selector:
    matchLabels:
      app: nginxApp
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginxApp
    spec:
      - containers:
          - name: nginx-container
            image: nginx:latest
            ports:
              - containerPort: 80
                protocol: "TCP"

   
```            

## Sample Service Template for Reference

```yml
apiVersion: v1
kind: Service
metadata:
  name: demo-service
spec:
  type: NodePort
  selector:
    app: demoapp
  ports:
    - name: http # service port name
      port: 80 # service port
      targetPort: 80 # container port
      nodePort: 30000 # node port
```      
