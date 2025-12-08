---
title: "Event 3"
date: "2025-11-15"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
# Summary Report: "AIML & Generative AI on AWS – AWS Cloud Mastery Series #1"

## Event Overview

| | |
|---|---|
| **Event Name** | AIML & Generative AI on AWS – AWS Cloud Mastery Series #1 |
| **Date** | November 15, 2025 |
| **Role** | Attendee |
| **Format** | On-site technical session |
| **Duration** | Full-day session (8:30 AM – 11:00 AM+) |
| **Location** | 26th floor, Bitexco Financial Tower, District 1, Ho Chi Minh City, Vietnam |

This comprehensive technical session was part of the AWS Cloud Mastery Series, focusing specifically on artificial intelligence, machine learning, and generative AI capabilities on AWS. The event provided both theoretical foundations and practical insights into building AI/ML solutions using AWS services.

---

## Session Agenda

### Session 1: AI/ML Overview (8:30 – 9:00 AM)
**Speaker:** Lam Tuan Kiet

#### Machine Learning Fundamentals
- **Supervised Learning:** Understanding tasks where models learn from labeled data
  - Classification: Categorizing data into classes
  - Regression: Predicting continuous values
  - Common algorithms and use cases
- **Deep Learning:** Neural networks and their applications
  - Multi-layer perceptrons
  - Convolutional Neural Networks (CNNs) for image processing
  - Recurrent Neural Networks (RNNs) for sequence data
  - Transformers architecture

#### Foundation Models and Generative AI
- **Foundation Models:** Large pre-trained models that serve as the base for various tasks
  - What makes a model a "foundation model"
  - Benefits of using pre-trained models
  - Transfer learning concepts
- **Generative Models:** Models that create new content
  - Understanding unsupervised learning in the context of generative AI
  - How generative models differ from discriminative models
  - Applications: text generation, image generation, code generation

#### Prompt Engineering
- **What is a prompt?:** Understanding prompts as instructions to AI models
- **Good vs Bad Prompts:**
  - Characteristics of effective prompts (clear, specific, contextual)
  - Common mistakes in prompt design
  - Examples of poorly constructed prompts and how to improve them
- **Zero-shot Prompting:** Getting results without examples
  - When zero-shot works well
  - Limitations and considerations
- **Few-shot Prompting:** Providing examples to guide model behavior
  - How few-shot learning improves results
  - Best practices for selecting examples
  - Balancing example quality and quantity

#### Chain of Thought Reasoning
- **What is Chain of Thought?:** Breaking down complex problems into steps
- **Benefits:** Improving reasoning capabilities of language models
- **Implementation:** How to structure prompts to encourage step-by-step thinking
- **Applications:** Problem-solving, mathematical reasoning, logical analysis

#### Retrieval-Augmented Generation (RAG)
- **RAG Overview:** Combining retrieval with generation for better accuracy
- **RAG Flow:**
  - Retrieval: Finding relevant information from knowledge bases
  - Augmentation: Enhancing prompts with retrieved context
  - Generation: Creating responses based on augmented prompts
- **Embeddings:**
  - What embeddings are and how they represent semantic meaning
  - Vector embeddings vs traditional keyword search
  - How embeddings enable semantic search
- **Amazon Titan Embeddings:**
  - AWS's embedding model capabilities
  - Use cases for Titan embeddings
  - Integration with other AWS services
- **RAG Workflows:**
  - Data Ingestion Workflow: Preparing and indexing documents for retrieval
    - Document processing and chunking
    - Generating embeddings
    - Storing in vector databases
  - Text Generation Workflow: Using RAG for query answering
    - Query processing and embedding
    - Similarity search
    - Context augmentation
    - Response generation

---

### Session 2: AWS AI/ML Services (9:00 – 10:00 AM)
**Speaker:** Dinh Le Hoang Anh

This session provided a comprehensive overview of AWS's managed AI/ML services beyond Amazon Bedrock, covering specialized services for different use cases.

#### Computer Vision Services

**Amazon Rekognition**
- **Image and Video Processing:** Analyzing visual content at scale
- **Object Recognition:** Identifying and labeling objects in images
- **Face Detection and Analysis:**
  - Detecting faces in images and videos
  - Face comparison and verification
  - Facial attribute analysis
- **Content Moderation:**
  - Detecting inappropriate or unsafe content
  - Custom moderation models
- **Celebrity Recognition:** Identifying well-known personalities
- **Custom Labeling:**
  - Training custom models for specific recognition tasks
  - Use cases for domain-specific image classification
  - Workflow for creating custom models

#### Natural Language Processing Services

**Amazon Translate**
- **Context-Aware Translation:** Understanding context for better translations
- **Real-time Translation:** Low-latency translation for applications
- **Language Identification:** Automatically detecting source language
- **Custom Terminology:** Using domain-specific translation glossaries
- **Batch Translation:** Processing large volumes of text

**Amazon Textract**
- **Optical Character Recognition (OCR):** Extracting text from images and documents
- **Layout Preservation:** Maintaining document structure and formatting
- **Form and Table Extraction:** Identifying and extracting structured data
- **Handwriting Recognition:** Processing handwritten text
- **Document Analysis:** Understanding document types and extracting key information

**Amazon Transcribe**
- **Speech-to-Text Conversion:** Converting audio to text
- **Speaker Identification:** Distinguishing between different speakers
- **Content Filtering:** Filtering inappropriate content in transcriptions
- **Custom Vocabulary:** Improving accuracy with domain-specific terms
- **Real-time Transcription:** Live transcription capabilities
- **Multi-language Support:** Transcribing in multiple languages

**Amazon Polly**
- **Text-to-Speech:** Converting text to natural-sounding speech
- **Voice Types:** Multiple voices and languages available
- **Real-time Synthesis:** Low-latency speech generation
- **Caching and Replay:** Optimizing for repeated content
- **SSML Support:** Advanced speech synthesis markup

**Amazon Comprehend**
- **Insight Extraction:** Understanding sentiment, entities, and key phrases
- **Relationship Extraction:** Identifying relationships between entities
- **Topic Modeling:** Discovering topics in document collections
- **Language Detection:** Identifying the language of text
- **Custom Classification:** Training custom text classifiers

#### Search and Discovery Services

**Amazon Kendra**
- **Semantic Search:** Understanding meaning, not just keywords
- **Intelligent Search:** NLP-powered search capabilities
- **RAG Support:** Integration with retrieval-augmented generation
- **Enterprise Search:** Searching across multiple data sources
- **Custom Data Sources:** Connecting to various content repositories

#### Recommendation Services

**Amazon Personalize**
- **Tailored Recommendations:** Creating personalized user experiences
- **Real-time Recommendations:** Low-latency recommendation generation
- **Batch Recommendations:** Processing recommendations for large user bases
- **Custom Models:** Training models on your data
- **A/B Testing:** Testing different recommendation strategies

#### Specialized Frameworks

**Pipecat**
- **Pipeline Framework:** Building voice and multimodal AI agents
- **Real-time Capabilities:** Optimized for real-time interactions
- **Use Cases:** Voice assistants, interactive applications
- **Integration:** Working with AWS services and other AI tools

**Amazon Lookout Family**
- *Note:* These services have been integrated into other AWS services
- **Historical Context:** Understanding what Lookout services provided
- **Migration Path:** How functionality moved to other services

---

### Session 3: Amazon Bedrock AgentCore (10:00 – 11:00 AM)
**Speaker:** Danh Hoang Hieu Nghi

This session focused on building AI agents using Amazon Bedrock AgentCore, covering both the concepts and practical implementation.

#### Agent Frameworks Overview
- **LangGraph:** Building stateful, multi-actor applications with LLMs
- **LangChain:** Framework for developing applications powered by language models
- **LlamaIndex:** Data framework for LLM applications
- **Comparison:** Understanding when to use each framework
- **Integration:** How these frameworks work with AWS services

#### Agent Creation Process
- **Planning Phase:** Defining agent goals and capabilities
- **Design Phase:** Architecting agent workflows and decision trees
- **Development Phase:** Implementing agent logic and integrations
- **Testing Phase:** Validating agent behavior and edge cases
- **Deployment Phase:** Putting agents into production

#### Production Challenges
- **Scalability:** Handling increasing load and concurrent users
- **Reliability:** Ensuring consistent performance and error handling
- **Monitoring:** Tracking agent performance and user interactions
- **Cost Management:** Optimizing costs while maintaining quality
- **Security:** Protecting sensitive data and preventing misuse

#### Amazon Bedrock AgentCore Keywords

**Runtime**
- Execution Environment: Where agents run and execute
- Performance Optimization: Ensuring fast response times
- Resource Management: Allocating and managing compute resources

**Memory**
- Conversation History: Maintaining context across interactions
- Long-term Memory: Storing information for future sessions
- Memory Management: Efficient storage and retrieval strategies

**Identity**
- User Identification: Identifying and authenticating users
- Session Management: Managing user sessions and state
- Multi-user Support: Handling multiple concurrent users

**Gateway**
- API Gateway: Exposing agents through APIs
- Integration Points: Connecting agents to other systems
- Request Routing: Directing requests to appropriate agents

**Code Interpreter**
- Code Execution: Running code within agent workflows
- Sandboxing: Safe execution environment
- Use Cases: Data analysis, calculations, dynamic content generation

**Browser Tool**
- Web Interaction: Enabling agents to interact with web content
- Information Retrieval: Fetching and processing web data
- Automation: Automating web-based tasks

**Observability**
- Monitoring: Tracking agent performance and behavior
- Logging: Recording agent interactions and decisions
- Analytics: Understanding agent usage patterns
- Debugging: Tools for troubleshooting agent issues

#### AgentCore Services for Scale
- **Multi-agent Systems:** Coordinating multiple agents
- **Load Balancing:** Distributing load across agent instances
- **Auto-scaling:** Automatically adjusting capacity
- **High Availability:** Ensuring agents are always available
- **Enterprise Features:** Security, compliance, and governance

---

## Key Technical Learnings

### AI/ML Fundamentals
- Clear understanding of the difference between traditional ML, deep learning, and generative AI
- How foundation models enable new types of applications
- The importance of prompt engineering in getting good results from generative models

### RAG Architecture
- Complete understanding of RAG workflows from data ingestion to text generation
- How embeddings enable semantic search and improve retrieval quality
- Practical knowledge of implementing RAG systems on AWS

### AWS Service Ecosystem
- Comprehensive overview of AWS AI/ML services and when to use each
- Understanding that different services solve different problems
- How services can be combined for complex solutions

### Agent Development
- Understanding the complexity of building production-ready AI agents
- Key components needed for scalable agent systems
- Best practices for agent design and deployment

---

## Personal Takeaways

### Technical Growth
- Gained a structured mental model of the modern GenAI stack on AWS
- Understand how RAG pipelines are built end-to-end, from data preparation to response generation
- Learned which managed services to combine when designing AI-powered applications

### Practical Insights
- The importance of prompt engineering cannot be overstated
- RAG is a powerful pattern for building accurate, context-aware AI applications
- AWS provides a comprehensive set of services that cover the entire AI/ML spectrum

### Future Applications
- Excited to build RAG-based applications using Amazon Bedrock and Titan embeddings
- Want to explore building agents using AgentCore for specific use cases
- See opportunities to combine multiple AWS AI services for comprehensive solutions

### Career Development
- This event reinforced my interest in AI/ML and generative AI
- Understand the breadth of opportunities in the AI space on AWS
- Motivated to continue learning about advanced AI/ML techniques and AWS services

---

## Event Experience

This was an incredibly informative event that provided both breadth and depth. The progression from fundamentals to specific services to advanced agent development gave me a complete picture of AI/ML on AWS.

The speakers were knowledgeable and provided practical insights beyond just feature descriptions. The real-world examples and use cases helped me understand how to apply these services in practice.

The event structure allowed for good pacing, with each session building on previous concepts. The combination of theory and practical examples made complex topics accessible.

#### Event Photos

![Event Overview - AI/ML/GenAI on AWS Workshop with audience](/images/event-3/workshop-overview.png) 

![Presentation Session](/images/event-3/demo-session.png)

![Kahoot Winners - Group photo with Kahoot quiz session](/images/event-3/kahoot-winners.png)

![Amazon AI Services Grid - Overview of AWS AI service portfolio](/images/event-3/ai-services-grid.png)

![RAG in Action - Retrieval Augmented Generation workflow diagram](/images/event-3/rag-in-action.png)

![Amazon Bedrock AgentCore - Comprehensive agentic platform announcement](/images/event-3/bedrock-agentcore.png)

![AgentCore Architecture - Services enabling agents at scale](/images/event-3/agentcore-architecture.png)

![RetrieveAndGenerate API - Knowledge Bases for Amazon Bedrock fully managed RAG](/images/event-3/retrieve-generate-api.png)

![Prototype to Production Chasm - Challenges on the path to production](/images/event-3/prototype-production-chasm.png)

![Frameworks for Building Agents - Embracing open source frameworks](/images/event-3/frameworks-agents.png)
