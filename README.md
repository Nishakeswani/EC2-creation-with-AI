# EC2-creation-with-AI
# Please find details of this project {https://medium.com/@nishakeswani}

Control AWS with hand gestures using Artificial Intelligence

Imagine a world where you can create Amazon Web Services (AWS) EC2 instances - those powerful virtual computers in the cloud - with just the wave of your hand. Well, you don't need to imagine anymore! 
In this blog post, we're going to explore a fun and practical project: creating a finger gesture-controlled Amazon EC2 (Elastic Compute Cloud) instance launcher using Python and AWS (Amazon Web Services). Let's get started.
Prerequisites
Before begin with this project, make sure you have the following:
Python installed on your computer.

To cross check whether Python is present on your system or not:

2. AWS CLI should be configured. 
You can download and install the AWS CLI from the official AWS CLI documentation.
3. AWS account with access keys and secret access key. Once you get the keys you can configure the AWS CLI as below:
4. Python library should be installed - boto3 , CV2 (opencv) , cvzone 
Let's dive into the code of this project
To create this project, we will be using python programming language as I already mentioned in pre-requisite.
This Python code combines computer vision and Amazon Web Services (AWS) to create this unique project. It uses OpenCV for capturing and analyzing live video from a webcam and the CVZone library to detect hand gestures. The program continuously displays the webcam feed, and when it recognizes specific hand gestures like raising all fingers, the code interacts with AWS using the Boto3 library to create EC2 instances.
import boto3
myec2 = boto3.resource("ec2"  )
def launchOS():
    response = myec2.create_instances( 
        ImageId="ami-0da59f1a", 
        InstanceType="t2.micro",
        MaxCount=1,
        MinCount=1
    )
import  cv2
cap = cv2.VideoCapture( 0 )
from cvzone.HandTrackingModule import HandDetector
detector = HandDetector()
while True:
    status , photo = cap.read()
    cv2.imshow("my photo" , photo)
    if cv2.waitKey(100) == 13:
        break
    
    handphoto = detector.findHands(photo , draw=False)
    
    if handphoto:
        lmlist = handphoto[0]
        fingerstatus = detector.fingersUp(lmlist)

        if fingerstatus == [1,1,1,1,1]:
            print("all up")
            launchOS()
            launchOS()
            launchOS()
            
    
        elif fingerstatus == [ 0 ,1 ,0 , 0, 0]:
            print("index finger up")
            launchOS()
    
        elif fingerstatus == [ 0 , 1, 1, 0 , 0 ]:
            print("index and middle finger up")
            launchOS()
            launchOS()
    
        else:
            print("idk")
            
cv2.destroyAllWindows()
cv2.destroyAllWindows()
cv2.release()

Once you write this program, you need to make few changes in this. for example, if  you want to create Windows EC2 instance, then you need to add Windows image ID: 
If you want different instance type , you can modify this as well according to the requirement. Similarly, you can set Min and Max count of the instances as well. 
Once you are done with all the requirements and when you run this python program and shows the index finger, EC2 instance gets created on AWS. 
Here, [0,1,0,0,0] represents position of the finger. 
Isn't it cool enough that you are now able to control AWS using hand gestures. 
In simpler terms, you can create these powerful cloud-based computers just by waving your hand in front of your webcam. It's like having a superpower, right from your computer!
This project isn't just about the "wow" factor. It shows how innovative technology can make our lives more convenient and fun.
This is not only a fascinating technical endeavor but also a valuable addition to your career and resume.
1. Career Application:
Cloud Computing Specialist: You can position yourself as a cloud computing specialist who has hands-on experience in AWS EC2 instance management, showcasing your ability to innovate and streamline cloud operations.
Computer Vision Engineer: This project highlights your skills in computer vision and gesture recognition, which are highly relevant in fields like robotics, augmented reality, and human-computer interaction.

2. Resume Enhancement:
Project Showcase:  Include this project prominently in your resume's projects or portfolio section. Describe it as a "Gesture-Controlled AWS EC2 Instance Launcher," emphasizing the innovation and technical skills involved.
Technical Skills: Highlight the technologies used, such as Python, OpenCV, CVZone, and AWS services, under your technical skills section.

3. LinkedIn Profile:
Update your LinkedIn profile to include this project. Share it as a LinkedIn post, emphasizing the practical applications and innovation.

This project is a powerful tool to showcase your skills, creativity, and passion for technology. It can open doors to opportunities in cloud computing, computer vision, and related fields.
