## What is AI?

https://learn.microsoft.com/en-us/training/modules/get-started-ai-fundamentals/1-introduction?WT.mc_id=academic-77998-cacaste

Simply put, AI is the creation of software that imitates human behaviors and capabilities. Key workloads include:

-   **Machine learning** - This is often the foundation for an AI system, and is the way we "teach" a computer model to make predictions and draw conclusions from data.
-   **Anomaly detection** - The capability to automatically detect errors or unusual activity in a system.
-   **Computer vision** - The capability of software to interpret the world visually through cameras, video, and images.
-   **Natural language processing** - The capability for a computer to interpret written or spoken language, and respond in kind.
-   **Knowledge mining** - The capability to extract information from large volumes of often unstructured data to create a searchable knowledge store.

## Understand machine learning

Sustainable farming techniques are essential to maximize food production while protecting a fragile environment. _The Yield_, an agricultural technology company based in Australia, uses sensors, data, and machine learning to help farmers make informed decisions related to weather, soil, and plant conditions.

## How machine learning works

Suppose an environmental conservation organization wants volunteers to identify and catalog different species of wildflower using a phone app. The following animation shows how machine learning can be used to enable this scenario.

1.  A team of botanists and scientists collect data on wildflower samples.
2.  The team labels the samples with the correct species.
3.  The labeled data is processed using an algorithm that finds relationships between the features of the samples and the labeled species.
4.  The results of the algorithm are encapsulated in a model.
5.  When new samples are found by volunteers, the model can identify the correct species label.

![[machine-learn.gif]]
![[Screen Shot 2023-04-30 at 9.08.20.png]]


## Understand anomaly detection

Imagine you're creating a software system to monitor credit card transactions and detect unusual usage patterns that might indicate fraud. Or an application that tracks activity in an automated production line and identifies failures. Or a racing car telemetry system that uses sensors to proactively warn engineers about potential mechanical failures before they happen.

These kinds of scenario can be addressed by using _anomaly detection_ - a machine learning based technique that analyzes data over time and identifies unusual changes.

![[anomaly-detection.gif]]

1.  Sensors in the car collect telemetry, such as engine revolutions, brake temperature, and so on.
2.  An anomaly detection model is trained to understand expected fluctuations in the telemetry measurements over time.
3.  If a measurement occurs outside of the normal expected range, the model reports an anomaly that can be used to alert the race engineer to call the driver in for a pit stop to fix the issue before it forces retirement from the race.

To learn more, view the [Anomaly Detector service web site](https://azure.microsoft.com/services/cognitive-services/anomaly-detector/).


# Understand computer vision

Computer Vision is an area of AI that deals with visual processing. Let's explore some of the possibilities that computer vision brings.

The **Seeing AI** app is a great example of the power of computer vision. Designed for the blind and low vision community, the Seeing AI app harnesses the power of AI to open up the visual world and describe nearby people, text and objects.

https://www.microsoft.com/es-mx/ai/seeing-ai?rtc=1

Image classification

![An image of a taxi with the label "Taxi"](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/image-classification.png)  
Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.


Object detection

![An image of a street with buses, cars, and cyclists identified and highlighted with a bounding box](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/object-detection.png)  
Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle.

Semantic segmentation

![An image of a street with the pixels belonging to buses, cars, and cyclists identified](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/semantic-segmentation.png)  
Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors.

Image analysis

![An image of a person with a dog on a street and the caption "A person with a dog on a street"](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/image-analysis.png)  
You can create solutions that combine machine learning models with advanced image analysis techniques to extract information from images, including "tags" that could help catalog the image or even descriptive captions that summarize the scene shown in the image.

Face detection, analysis, and recognition

![An image of multiple people on a city street with their faces highlighted](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/face-analysis.png)  
Face detection is a specialized form of object detection that locates human faces in an image. This can be combined with classification and facial geometry analysis techniques to recognize individuals based on their facial features.

Optical character recognition (OCR)

![An image of a building with the sign "Toronto Dominion Bank", which is highlighted](https://learn.microsoft.com/en-us/training/wwl-data-ai/get-started-ai-fundamentals/media/ocr.png)  
Optical character recognition is a technique used to detect and read text in images. You can use OCR to read text in photographs (for example, road signs or store fronts) or to extract information from scanned documents such as letters, invoices, or forms.

# Understand natural language processing

Natural language processing (NLP) is the area of AI that deals with creating software that understands written and spoken language.

NLP enables you to create software that can:

-   Analyze and interpret text in documents, email messages, and other sources.
-   Interpret spoken language, and synthesize speech responses.
-   Automatically translate spoken or written phrases between languages.
-   Interpret commands and determine appropriate actions. 

![[Screen Shot 2023-04-30 at 19.52.06.png]]

# Understand knowledge mining


Knowledge mining is the term used to describe solutions that involve extracting information from large volumes of often unstructured data to create a searchable knowledge store.


Azure Cognitive Search can utilize the built-in AI capabilities of Azure Cognitive Services such as image processing, content extraction, and natural language processing to perform knowledge mining of documents. The product's AI capabilities makes it possible to index previously unsearchable documents and to extract and surface insights from large amounts of data quickly.

![[Screen Shot 2023-04-30 at 19.59.41.png]]

# Understand Responsible AI
AI systems should treat all people fairly. For example, suppose you create a machine learning model to support a loan approval application for a bank. The model should predict whether the loan should be approved or denied without bias. This bias could be based on gender, ethnicity, or other factors that result in an unfair advantage or disadvantage to specific groups of applicants.

## Reliability and safety

AI systems should perform reliably and safely. For example, consider an AI-based software system for an autonomous vehicle; or a machine learning model that diagnoses patient symptoms and recommends prescriptions. Unreliability in these kinds of systems can result in substantial risk to human life.

## Privacy and security

AI systems should be secure and respect privacy. The machine learning models on which AI systems are based rely on large volumes of data, which may contain personal details that must be kept private. Even after the models are trained and the system is in production, privacy and security need to be considered. As the system uses new data to make predictions or take action, both the data and decisions made from the data may be subject to privacy or security concerns.

## Inclusiveness

AI systems should empower everyone and engage people. AI should bring benefits to all parts of society, regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.

## Transparency

AI systems should be understandable. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.

## Accountability

People should be accountable for AI systems. Designers and developers of AI-based solutions should work within a framework of governance and organizational principles that ensure the solution meets ethical and legal standards that are clearly defined.

## Further resources
[https://www.microsoft.com/ai/responsible-ai-resources](https://www.microsoft.com/ai/responsible-ai-resources).


# Introduction to AI


