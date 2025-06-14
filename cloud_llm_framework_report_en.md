## Generative AI Deployment Solution Research Report v2.0

## Table of contents

1. Executive Summary
2. Decision Dimensions and Scoring Model
3. Deployment Mode Overview
4. Startup Free Credits Summary
5. Detailed plan comparison

- 4.1 International/Domestic Third-Party API
- 4.2 Cloud vendor managed reasoning
- 4.3 Low-code/scheduling platform and framework
- 4.4 Self-hosted open source model

6. Three-year TCO simulation
7. Risk and compliance assessment
8. Implementation Roadmap
9. Conclusion and next steps
10. References

---

## 1. Executive Summary

This report aims to provide a clear, phased strategic roadmap for startup teams in the deployment and selection of generative AI.
The core conclusion is that successful AI application deployment should follow an incremental evolution path to balance innovation speed, service stability, and long-term cost-effectiveness.

![Generative AI Deployment Strategy Roadmap](./pictures/roadmap.png)

**PoC Phase (Proof of Concept)**

- Recommended solution: third-party API + low-code platform (such as Dify/Coze).
- Reason: With limited time and resources, the plug-and-play capabilities of third-party APIs combined with the visual process of low-code platforms can produce demonstrable prototypes within days to weeks, verifying business models and user needs with minimal investment. Using free quotas or startup plans from manufacturers, early costs can be almost negligible.
  **Beta phase (public testing and iteration period)**
- Recommended solution: Migrate to mainstream cloud vendors' managed services (such as Azure OpenAI / AWS Bedrock), and integrate professional vector databases (such as Pinecone, Milvus) to build RAG applications.
- Reason: With the growth of user volume and functional requirements, higher availability, elastic expansion and compliance assurance are required. Cloud hosting services can quickly deploy stable endpoints, seamlessly integrate with cloud monitoring, security, storage and other services, meet SLA and domestic data residency requirements, and verify medium-scale carrying capacity within a controllable cost range.
  **Scale Phase (Scaling and Optimization Phase)**
- Recommended solution: Build a self-hosted GPU cluster + API hybrid scheduling architecture.
- Reason: When the call volume reaches millions/month or higher, the cost of third-party API or cloud hosting pay-as-you-go model rises rapidly. Self-hosted GPU clusters can significantly reduce unit costs at high utilization; combined with third-party APIs as an alternative for peak or special high-performance requirements, hybrid scheduling is formed to achieve a balance between cost and performance. At this stage, mature MLOps capabilities, improved monitoring and compliance audit systems are required to ensure the stability and security of large-scale services.

---

## 2. Decision Dimensions and Scoring Model

In order to achieve a scientific and transparent selection process, a quantitative evaluation model was established, which includes the following six key dimensions. Each dimension is assigned a weight that reflects the typical priorities of start-ups.
![Decision Dimension](./pictures/decision.png)

| Dimensions                           | Weights | Description and Considerations                                                                                                                                                                                                                                                                                          |
| ------------------------------------ | :-----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Speed ​​to market                    |   25%   | Core question: How quickly can we get our product to users? Evaluate the integration difficulty and end-to-end delivery cycle of the solution. For startups, quickly launching an MVP is the key to gaining a head start in the market.                                                                                 |
| Long-term costs                      |   20%   | Core question: Will our profits be eaten up by costs after scaling? Focus on 3-year TCO, including API call fees, hardware depreciation, operation and maintenance manpower, upgrade and migration costs, etc., to measure long-term sustainability and profit margin impact.                                           |
| Operation and maintenance complexity |   15%   | Core question: How many people and what skills are needed to maintain the system? Evaluate the workload of daily maintenance, monitoring, troubleshooting and upgrades. Low operation and maintenance solutions allow streamlined teams to focus more on business innovation.                                           |
| Elastic expansion                    |   15%   | Core question: Can the system support a sudden increase in the number of users? Can the cost be reduced during off-peak hours? The flexibility of the automatic expansion capability and automatic reduction cost saving of the solution directly affects the cost efficiency and user experience.                      |
| Ecosystem completeness               |   15%   | Core question: How easy is it to build advanced features such as RAG and Agent? Investigate the maturity of surrounding tool chains, development libraries, and community support. A complete ecosystem can greatly reduce the difficulty of building complex AI applications and accelerate development and iteration. |
| Compliance and Security              |   10%   | Core Questions: Does the solution meet local regulations? Is user data secure? Evaluating data residency, content review, privacy protection, encryption and audit capabilities is critical for projects targeting specific industries or regions.                                                                      |

**illustrate:**

- Weights can be adjusted at different stages. In the PoC stage, the weight of "online speed" can be increased to ~35%; in the Scale stage, the weights of "long-term cost" and "elastic expansion" can be increased.

---

## 3. Overview of deployment modes

![Deployment mode](./pictures/compare.svg)
| Solution | Typical vendors/tools | Cost model | Speed ​​of launch | Operation and maintenance complexity | Ecosystem integrity | Compliance | Recommended stage |
| ----------- | -------------------------------------- | ----------------------- | ----------------- | -------------------- | --------------------- | -------------------------- | -------- |
| Third-party API | OpenAI, Anthropic, Ali Qwen, DeepSeek | On-demand token billing | ⭐⭐⭐⭐⭐ (fastest) | ⭐⭐⭐⭐⭐ (zero operation and maintenance) | ⭐⭐⭐⭐⭐ (open ecosystem) | International version ❌<br>Domestic version ✅ | PoC |
| Cloud-hosted reasoning | Azure OpenAI, AWS Bedrock, Alibaba Bailian | On-demand token/reserved instance | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐☆ | ⭐⭐⭐⭐⭐ (closed-loop ecosystem) | ✅ (domestic nodes optional) | Beta |
| Low code/framework | Dify, Coze, LangChain, CrewAI | Subscription + usage (cost penetration) | ⭐⭐⭐⭐⭐ (fastest) | ⭐⭐⭐⭐☆ (relatively simple) | ⭐⭐⭐⭐☆ (integrated ecosystem) | Self-hosted ✅<br>SaaS version needs to be evaluated | PoC➜Beta |
| Self-hosted GPU | RunPod, CoreWeave, BentoML Cloud | Fixed computing cost (GPU hourly rental) | ⭐⭐☆☆☆ | ⭐☆☆☆☆ (most complex) | ⭐⭐⭐☆☆ (self-built) | ✅ (self-responsibility) | Scale |

**illustrate:**

- Third-party API: Fastest launch, no infrastructure operation and maintenance required; low initial cost, high linear cost in the later stage; international version has data outflow and compliance risks.
- Cloud-hosted inference: easy to deploy, elastically scalable, and deeply integrated with the cloud ecosystem; optional domestic Region to satisfy data residency; suitable for medium-sized and compliance-required scenarios.
- Low-code platform/framework: Visualized processes or modular components, built-in RAG/Agent functions, suitable for rapid verification; SaaS version requires evaluation of data storage; self-hosted version or open source framework can be fully controlled.
- Self-hosted GPU: Lowest long-term cost, highly customizable, highest data sovereignty, but with the highest technical threshold and operation and maintenance complexity, suitable for mature stages and high-concurrency scenarios.

---

## 4. Startup Free Credits and related benefits summary

| Name/Manufacturer                       | Plan/Project                                           | Amount (RMB ¥ / USD $ / Free)                                                        | Application Points                                                             | Support Content/Usage Suggestions                                                                                                                                                                                                                                                      |
| --------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AWS Activate                            | Startup Acceleration (including Generative AI Special) | ¥72,500–¥2,175,000 (~$1k–$300k)                                                      | New startup conditions; VC/incubator recommendations available                 | - Special quota can be used to test AI hardware such as Trainium/Inferentia\<br\>- Covers all AWS cloud services and AI/ML services (such as Amazon Bedrock, SageMaker)\<br\>- Provides technical support, training and guidance                                                       |
| Azure Founders Hub                      | Entrepreneur Center                                    | ¥36,000–¥1,087,500 (~$5k–$150k)                                                      | No VC recommendation required; renewal based on usage activity                 | - Credits can be used for various Azure services (Azure OpenAI, storage, computing, database, etc.)\<br\>- Includes GitHub Enterprise, Microsoft 365 developer licenses\<br\>- Provides technical guidance and entrepreneurial ecosystem connections                                   |
| Google for Startups                     | Cloud Program                                          | ¥14,500–¥2,537,500 (~$2k–$350k)                                                      | VC recommendation required; business/technical plans to be submitted in phases | - Start Tier ($2k) for ideation phase\<br\>- Scale Tier ($200k, two-year term) requires financing and scale conditions\<br\>- AI First ($350k) covers $250k of usage in the first year, discounted renewal in the second year\<br\>- Covers Vertex AI and other GCP AI/ML services     |
| Alibaba Cloud MARS Entrepreneur Program | Cloud Discount Coupons                                 | ¥3.5k–¥1 million                                                                     | Individual businesses or start-ups can apply                                   | - AI resource subsidies: trillions of tokens-level call subsidies, thousands of hours of technical support\<br\>- Expert 1v1 docking service, technical training camp, investment and financing resource docking\<br\>- Covers AI services such as Tongyi Qianwen Model and DashVector |
| Tencent Cloud Lite model is free        | Hunyuan Lite / Intelligent Agent Development Platform  | Free tokens, character capacity, knowledge base, etc.                                | Complete real-name authentication and activate                                 | - Hunyuan Lite model is permanently free, with no quota limit\<br\>- 500,000 tokens (2 months) will be given for the first opening of the Intelligent Agent Development Platform\<br\>- Suitable for concept verification and early development testing                                |
| Baidu Qianfan Entrepreneur Program      | Entrepreneur Program                                   | Free/Enterprise Special 50 million Tokens                                            | After enterprise certification, you can apply for flagship model quota         | - ERNIE Speed/Lite is completely free and has no usage restrictions\<br\>- Enterprise users can apply for ERNIE3.5 flagship model 50 million Tokens for free call\<br\>- Support vector library integration, Agent Builder low-code development                                        |
| Anthropic for Startups                  | Claude API Verification                                | Free API credits, higher rate limits, community support, exclusive event invitations | Usually requires VC/accelerator endorsement                                    | - Covers Claude 3 series model calls\<br\>- Suitable for verifying Claude model capabilities and early prototype development                                                                                                                                                           |
| Mistralship (Mistral AI)                | La Plateforme Visit                                    | 6-month startup plan, providing about $30k credits                                   | In line with the early stage of financing                                      | - PoC stage to verify the capabilities of Mistral model; Beta stage evaluation and comparison with other models to decide on long-term cooperation                                                                                                                                     |
| Vercel AI Accelerator                   | Front-end + AI application acceleration                | \~$4,000,000+ credits                                                                | Project matching conditions; cycle about 6 weeks, about 40 teams               | - Suitable for teams that quickly build front-end + AI applications\<br\>- End-to-end verification with full range of credits                                                                                                                                                          |
| Together AI Studio                      | Comprehensive cloud credits                            | Commitment of $1,000,000 in funding and \>$600,000 in cloud credits                  | Pay attention to the project application period                                | - Teams with innovative AI application ideas can apply and receive comprehensive support                                                                                                                                                                                               |

---

## Detailed analysis of international cloud platform benefits

### AWS Activate – Significant Improvement in Generative AI

- **Special Funding**: Up to $300,000 (approximately ¥2.175 million) specifically for testing AI acceleration hardware such as AWS Trainium/Inferentia.
- **Grading application conditions**:
- **Activate Founders**: Base $1,000 (about ¥72,500), suitable for self-funded or early-stage teams.
- **Standard startup**: Up to $100,000 (approximately ¥725,000), VC/incubator recommendation or partner institution endorsement required.
- **Generative AI Specialty**: Up to $300,000 (approximately ¥2.175 million), focusing on generative AI-related business or technology verification scenarios.
- **Basic Requirements**:
- New to AWS Activate, typically 10 years old or younger.
- Have financing record or viable business plan in the last 12 months.
- Complete company website, business registration information, team introduction and other materials.
- **Application website:** https://aws.amazon.com/activate/

### Azure Founders Hub – Lowest threshold, participation score

- **Initial amount**: Starting level $5,000 (approximately ¥36,000).
- **Growth Level**: You can apply for up to $25,000 (approximately ¥180,000), and you need to complete a verification checklist (such as usage, verification cases, etc.).
- **High Level**: Up to $150,000 (approximately ¥1.0875 million), automatically renewed by using an activity scoring system.
- **Features**:
- No VC recommendation required, self-service online application, fast review.
- Engagement score: About 45 days before the credit expires, we will automatically evaluate whether to renew or increase your credit based on your Azure service usage activity.
- Credits can be used for various Azure services, including Azure OpenAI, storage, computing, databases, etc.
- **Application website:** https://www.microsoft.com/en-us/startups

### Google for Startups – Highest Funding, AI-First Strategy

- **Three-tier support system**:

1. Start Tier: $2,000 (about ¥14,500) initial amount, for teams that have not received any or little funding.
2. **Scale Tier (Standard Startup)**: $200,000 (approximately ¥1.45 million) for two years, subject to meeting financing and company size requirements (such as Pre-seed/Seed/A round, etc.).
3. AI-First Startups: Up to $350,000 (approximately ¥2.5375 million), specifically for core AI technology startups that are required to provide AI-related business or technology plans.

- **AI Priority Program Additional Benefits**:
- Cover up to $250,000 in usage in the first year, and renew at a 20% discount in the second year.
- Additional special support: such as $10,000 for partner LLM model calls, $12,000 Google Cloud enhanced support credit, etc.
- **Application points**:
- You need to submit company information, financing proof (such as VC investment proof), technology/business plan, etc.
- The quotas at different stages are issued in phases, and subsequent support is evaluated based on milestones or usage.
- **Application website:** https://cloud.google.com/startup

---

## China Cloud Platform Support Plan

### Alibaba Cloud MARS Entrepreneur Program – Major Upgrade in 2025

- **Release background**: In April 2025, the "MARS Entrepreneur Program" was newly upgraded, aiming to support at least 1,000 start-ups within one year and provide millions of AI resource subsidies.
- **Core Support Content**:
- **AI resource subsidies**: Massive call subsidies (trillions of tokens) and thousands of hours of technical support.
- **Basic credit limit**: starting from ¥3,500, up to ¥1 million cloud discount coupons.
- **Expert Service**: Free 1v1 technical expert matching service.
- **Ecological support**: technical training camps, investment and financing resource docking, partner network, etc.
- **Application Requirements**:
- Both enterprises and individual businesses can apply, and they must not have paid for Alibaba Cloud or be applying for a special plan for the first time.
- Submit company/team information, business plan, AI technology roadmap, etc.; the review period is approximately 15-20 working days.
- **Usage suggestions**:
- Priority will be given to applying for and consuming subsidy resources for model calling and integration testing during the PoC/Beta phase.
- Plan the subsequent payment or renewal plan in advance based on usage, and compare and evaluate multi-cloud solutions by combining AWS/Azure/Google.
- Participate in official training camps and ecological activities to obtain more technical and financing support.
- **Application website:** https://help.aliyun.com/document_detail/2698335.html

### Tencent Cloud Lite model is free

- **Free form**: The Hunyuan Lite model is permanently free, with no usage limit, and the API input and output length is upgraded from 4k to 256k.
- **Free Quota**:
- The first time you activate the Hunyuan Large Model service, you will be given 1 million tokens (1 year). When you first activate the Intelligent Agent Development Platform, you will receive a free call quota of 500,000 tokens (valid for 2 months), which is applicable to the Hunyuan Large Model series and other fine-tuned knowledge large models.
- The Hunyuan Lite model has no limit on usage and can be used for free forever.
- Free knowledge base capacity of 3 million characters (valid for 6 months) and 5,000 online search calls (valid for 2 months).
- **Application Requirements**:
- Complete corporate or personal real-name authentication.
- After logging into the Tencent Cloud Intelligent Development Platform for the first time, click "Product Experience" to automatically activate and obtain free quota.
- **Usage suggestions**:
- Free quotas are used first, and consumption can be checked on the billing management page of the intelligent agent development platform.
- Suitable for startups or individuals to conduct proof of concept and early development testing.
- Free resources that are not used up after the expiration date will become invalid. It is recommended to use them in time or purchase renewals according to needs.
- **Application website:**https://cloud.tencent.com/document/product/1729/97731

### Baidu Qianfan Entrepreneur Program

- **Totally Free Strategy**: ERNIE Speed/Lite models are completely free for all users to use, with no usage restrictions.
- **Enterprise Special Quota**: After enterprise certification, you can apply for a free quota of 50 million Tokens of the ERNIE3.5 flagship model for use in production or testing environments.
- **How ​​to apply**:
- Register a Baidu Smart Cloud account and complete enterprise real-name authentication.
- Receive basic free quota on the Qianfan platform free activation page; submit enterprise information to apply for special quota.
- **Application website:** https://cloud.baidu.com/doc/WENXINWORKSHOP/s/xlxuhovgi

---

## Benefits for AI-focused service providers

### Anthropic for Startups

- **Support content**: Launch startup programs with VC partners, provide free API credits, higher rate limits, community support, exclusive founder event invitations, etc.
- **Application requirements**: Usually endorsed by a cooperating VC or accelerator, and submission of project plans and team information.
- **Usage suggestion**: Apply for credits when validating the capabilities of the Claude model; compare performance and cost with other models during the Beta phase.
- **Application website:** https://www.anthropic.com/startups

### Mistralship (Mistral AI)

- **Support Content**: 6-month startup program providing ~$30k credits to several startups for La Plateforme; 1:1 support; early access to new models and products.
- **Application conditions**: The team must meet the early financing stage and submit AI application scenarios and technical solutions.
- **Usage suggestions**: Verify the capabilities of the Mistral model in the PoC phase; evaluate and compare with other models in the Beta phase to decide on long-term cooperation.
- **Application website:** https://share-eu1.hsforms.com/12yGDfL7gQBCs-Jub4AonKw2dffx9

---

## Benefits for Professional Accelerator Entrepreneurs

### Vercel AI Accelerator

- **Project duration**: Approximately 6 weeks, providing over $4,000,000 in credits and resources to ~40 teams.
- **Main Benefits**:
- AWS offers $1,000,000 Activate credits
- Anthropic offers $600,000 credits + 3 months free Claude for Teams
- $430,000 credits from OpenAI
- Credits and support from 20+ other AI platforms
- **Usage suggestions**: Teams that intend to quickly build front-end + AI applications can apply for end-to-end verification with full range of credits.
- **Application website:** https://vercel.com/ai-accelerator

### Together AI Studio

- **Support**: $1,000,000 in funding and >$600,000 in cloud credits from OpenAI, AWS, Google Cloud, Azure, and more.
- **Usage suggestions**: Teams with innovative AI application ideas can follow this project and apply for comprehensive support.
- **Application website:**: https://together.fund/ai/

## 5. Detailed plan comparison

#### 5.1 International/Domestic Third-Party API

##### 5.1.1 Pricing Overview

| Platform / Model                      | Context Window (Tokens) | Input ¥ / 1k Tokens                         | Output ¥ / 1k Tokens                    | Features and Model Value                                                                                                                                  |
| ------------------------------------- | ----------------------- | ------------------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OpenAI**                            |                         |                                             |                                         |                                                                                                                                                           |
| GPT-4.1 nano                          | 128K                    | 0.00073                                     | 0.00290                                 | The fastest and lowest cost model, suitable for low-latency tasks such as fast-response agents or edge computing.                                         |
| GPT-4.1 mini                          | 128K                    | 0.00290                                     | 0.01160                                 | A balance between intelligence and speed, suitable for most medium-complexity business applications.                                                      |
| GPT-4.1                               | 128K                    | 0.01450                                     | 0.05800                                 | Most intelligent, suitable for complex tasks such as document understanding, legal analysis, research reasoning, etc.                                     |
| o3                                    | 128K                    | 0.01450                                     | 0.05800                                 | A new generation flagship reasoning model that excels at code, math, science, and multimodal reasoning tasks.                                             |
| o4-mini                               | 128K                    | 0.00798                                     | 0.03190                                 | The best performance-price ratio for inference, suitable for cost-sensitive mathematical and visual scenarios that require strong inference capabilities. |
| **Anthropic Claude**                  |                         |                                             |                                         |                                                                                                                                                           |
| Claude Haiku 3.5                      | 200K                    | 0.00580                                     | 0.02900                                 | Extreme cost-effectiveness and responsiveness, suitable for lightweight dialogue and real-time content generation scenarios.                              |
| Claude Sonnet 4                       | 200K                    | 0.02180                                     | 0.10875                                 | Optimal balance between intelligence and cost, suitable for enterprise-level search, RAG applications, daily AI assistants, etc.                          |
| Claude Opus 4                         | 200K                    | 0.10875                                     | 0.54375                                 | The most powerful intelligent model, suitable for the most complex reasoning, cross-modal applications and high-value task scenarios.                     |
| **Google (Gemini)**                   |                         |                                             |                                         |                                                                                                                                                           |
| Gemini 2.5 Flash Preview              | 1M                      | 0.00109                                     | 0.00435(Non-thinking) 0.02538(thinking) | Low-cost and long-context, optimal for multimodal scenarios; commonly used for high-concurrency and large-scale deployment.                               |
|                                       |
| Gemini 2.5 Pro                        | 1M                      | 0.00906 (≤200K)                             | 0.07250 (≤200K)                         | Deep document understanding and long document summarization, complex multimodal high-value scenarios.                                                     |
|                                       |                         | 0.01813 (>200K)                             | 0.10875 (>200K)                         |                                                                                                                                                           |
| **DeepSeek**                          |                         |                                             |                                         |                                                                                                                                                           |
| DeepSeek-V3                           | 64K                     | 0.00200 (miss)                              | 0.00800                                 | General MoE, cost-effective, excellent Chinese comprehension and reasoning; cache hit can be reduced to 0.00051.                                          |
| DeepSeek-R1                           | 64K                     | 0.00400 (missed)                            | 0.01600                                 | Optimized version for complex reasoning, suitable for technical problem solving and deep thinking.                                                        |
| **Alibaba Cloud (Qwen)**              |                         |                                             |                                         |                                                                                                                                                           |
| Tongyi Qianwen-Max                    | 131,072                 | ¥0.0024                                     | ¥0.0096                                 | Flagship model, suitable for complex tasks, with the strongest capabilities                                                                               |
| Tongyi Qianwen-Plus                   | 131,072                 | ¥0.0008                                     | ¥0.0020                                 | Balanced effect, speed and cost, suitable for most general tasks                                                                                          |
| Tongyi Qianwen-Turbo                  | 1,000,000               | ¥0.0003                                     | ¥0.0006                                 | Extremely cost-effective, fast speed, low cost, suitable for simple tasks                                                                                 |
| Tongyi Qianwen-Long                   | 10,000,000              | ¥0.0005                                     | ¥0.0020                                 | Supports very long texts, suitable for large-scale analysis and long document processing scenarios                                                        |
| **Baidu Qianfan**                     |                         |                                             |                                         |                                                                                                                                                           |
| ERNIE Speed/Lite                      | 8K/128K                 | 0.00000 (Free)                              | 0.00000 (Free)                          | Lightweight and zero-cost, suitable for large-scale free trials and PoC.                                                                                  |
| ERNIE 4.5 Turbo                       | TBC                     | 0.00080                                     | 0.00320                                 | Cost-effective general model, supports tool calls, commonly used in enterprises.                                                                          |
| ERNIE 4.5                             | TBC                     | 0.00400                                     | 0.01600                                 | Deep multimodal flagship, leading in Chinese understanding and reasoning, and optimized for core business scenarios.                                      |
| **Tencent Cloud (Hunyuan)**           |                         |                                             |                                         |                                                                                                                                                           |
| Hunyuan-lite                          | 250K                    | 0.00000 (free)                              | 0.00000 (free)                          | Free long context, suitable for large-scale basic services and PoC.                                                                                       |
| Hunyuan-TurboS                        | 28K                     | 0.00080 (500,000-1,000,000 tokens are free) | 0.00200                                 | Trillion-parameter flagship, long-context high-performance scenarios.                                                                                     |
| Hunyuan-T1                            | 28K                     | 0.00100                                     | 0.00400                                 | General main model, comprehensive capabilities, suitable for core applications such as complex question answering and document understanding              |
| **Mistral AI**                        |                         |                                             |                                         |                                                                                                                                                           |
| Mistral Small 3.1                     | 128K                    | 0.00073                                     | 0.00218                                 | Lightweight and efficient, multi-language scenarios.                                                                                                      |
| Mistral Medium 3                      | 128K                    | 0.00290                                     | 0.01450                                 | Cost-effective for medium to high-complexity tasks, commonly used in coding/STEM.                                                                         |
| Mistral Large                         | 128K                    | 0.01450                                     | 0.04350                                 | Flagship level, suitable for the most demanding scenarios.                                                                                                |
| **Cohere**                            |                         |                                             |                                         |                                                                                                                                                           |
| Command R7B                           | 128K                    | 0.00027                                     | 0.00109                                 | Small model lightweight testing and lightweight RAG, lowest cost.                                                                                         |
| Command R                             | 128K                    | 0.00109                                     | 0.00435                                 | General RAG model, enterprise lightweight application.                                                                                                    |
| Command A                             | 256K                    | 0.01813                                     | 0.07250                                 | Agentic AI optimized version, suitable for multi-language RAG and complex business.                                                                       |
| **Volcano Ark (Volcengine)**          |                         |                                             |                                         |                                                                                                                                                           |
| Doubao-pro-32k                        | 32K                     | 0.00080                                     | 0.00200                                 | Main general-purpose large model, with high performance and accuracy.                                                                                     |
| **OpenRouter (Convergence Platform)** |                         |                                             |                                         |                                                                                                                                                           |
| Llama 3.3 70B                         | 131K                    | 0.00051                                     | 0.00181                                 | Lowest unit price, OpenAI compatible API, multi-vendor multi-model selection.                                                                             |

#### 5.1.2 Detailed description

---

### OpenAI Series

#### GPT-4.1 nano

- **Positioning and Tasks**: Ultra-low latency and ultra-low cost, suitable for edge computing, lightweight Agent, and Webhook callback scenarios that require extremely high response speed.
- **Cost-effectiveness analysis**: Only ¥0.00073/1k input, ¥0.00290/1k output, irreplaceable under millisecond-level interaction requirements.

#### GPT-4.1 mini

- **Positioning and Tasks**: A choice that balances intelligence and speed, suitable for medium-complexity customer service conversations, FAQ robots, and content review pipelines.
- **Cost-effectiveness analysis**: ¥0.00290 /1k input, ¥0.01160 /1k output, slightly higher than nano but with significantly improved inference quality.

#### GPT-4.1

- **Positioning and Mission**: Flagship intelligence, oriented to long text understanding, legal/financial document analysis, and in-depth research report writing.
- **Cost-effectiveness analysis**: ¥0.01450 /1k input, ¥0.05800 /1k output, suitable for core businesses with sufficient budget and quality priority.

#### o3

- **Localization and Tasks**: Top-notch multimodal reasoning models, good at code generation, mathematical proofs, scientific experiment design, and image understanding.
- **Cost-effectiveness analysis**: The price is the same as GPT-4.1 (¥0.01450/¥0.05800), but it has obvious advantages in professional benchmarks (MATH, Codeforces, ImageNet).

#### o4 mini

- **Location and Task**: Lightweight reasoning players with strong math, coding and visual understanding skills, suitable for cost-sensitive complex tasks.
- **Cost-effectiveness analysis**: ¥0.00798/1k input, ¥0.03190/1k output, ≈45% price reduction compared to o3, while still maintaining 80%+ performance.

---

### Anthropic Claude Series

#### Claude Haiku 3.5

- **Positioning and Task**: Extremely high-throughput, low-latency conversational model, designed for real-time customer service, content review, and fast summarization.
- **Cost-effectiveness analysis**: ¥0.00580/1k input, ¥0.02900/1k output, which is continuously stable in high-concurrency scenarios.

#### Claude Sonnet 4

- **Positioning and tasks**: An enterprise-level balanced flagship, suitable for RAG, search recommendation, and multi-round hybrid text + chart analysis.
- **Price/performance analysis**: ¥0.02180/1k input, ¥0.10875/1k output, providing high-quality experience for multi-modal and complex applications.

#### Close Work 4

- **Positioning and Mission**: Top thinker, focusing on cutting-edge research, strategic planning, cross-disciplinary comprehensive Q&A and creative writing.
- **Cost-effectiveness analysis**: ¥0.10875/1k input, ¥0.54375/1k output, reserved only for the most demanding inference quality scenarios.

---

### Google Gemini Series

#### Gemini 2.5 Flash Preview

- **Location and Task**: Low-cost long context + hybrid reasoning, supporting text/image/video/audio input, suitable for large-scale batch multimodal pipelines.
- **Cost-effectiveness analysis**: ¥0.00109/1k input, ¥0.00435/1k non-inference output, ¥0.02538/1k inference output, the optimal throughput cost.

#### Gemini 2.5 Pro

- **Location and Task**: The flagship of multimodal deep reasoning, supporting complex document understanding, code auditing, cross-media search and RAG.
- **Cost-effectiveness analysis**: ¥0.00906–¥0.01813 /1k input, ¥0.07250–¥0.10875 /1k output, unique pricing supports dynamic segmentation, taking into account short/long prompts.

---

### DeepSeek Series

#### DeepSeek-V3

- **Positioning and Task**: Cost-effective general Chinese MoE, suitable for article generation, summarization and general knowledge question and answering.
- **Cost-effectiveness analysis**: ¥0.00200/1k input, ¥0.00800/1k output for a miss; reduced to ¥0.00051 for a cache hit, significantly saving the cost of repeated queries.

#### DeepSeek-R1

- **Positioning and Tasks**: An enhanced version for complex reasoning, optimized for technical document analysis, scientific research assistance, and rigorous logical reasoning scenarios.
- **Cost-effectiveness analysis**: ¥0.00400 /1k input, ¥0.01600 /1k output, performance improvement to match professional needs.

---

### Alibaba Cloud Qwen Series

#### General Questions-Max

- **Positioning and Mission**: Flagship complex task expert, focusing on financial auditing, legal compliance, and in-depth analysis of scientific research literature.
- **Cost-effectiveness analysis**: ¥0.0024/1k input, ¥0.0096/1k output, achieving top-level model capabilities at a very low cost.

#### Tongyi Qianwen-Plus

- **Positioning and Tasks**: A balanced all-around model suitable for most mixed business scenarios—dialogue, summary, classification, RAG.
- **Cost-effectiveness analysis**: ¥0.0008/1k input, ¥0.0020/1k output, it is the most widely used "preferred base" in China.

#### Tongyi Qianwen-Turbo

- **Positioning and tasks**: An extremely fast and low-cost pipeline player, suitable for high-concurrency log decomposition, indicator extraction, and structured field extraction.
- **Cost-effectiveness analysis**: ¥0.0003/1k input, ¥0.0006/1k output, the lowest unit cost among all business models.

#### Tongyi Qianwen-Long

- **Positioning and Tasks**: An expert in processing very long texts, supporting 10M Tokens, and specially designed for building indexes and full-text retrieval for large-scale documents.
- **Cost-effectiveness analysis**: ¥0.0005/1k input, ¥0.0020/1k output, solving ultra-large contexts with the lowest cost.

---

### Baidu Qianfan ERNIE series

#### ERNIE Speed / Lite

- **Positioning and tasks**: Zero-cost entry, suitable for PoC, developer learning, and lightweight batch text processing.
- **Cost-effectiveness analysis**: Permanently free, no token restrictions, the first choice for trial and error and learning.

#### ERNIE 4.5 Turbo

- **Positioning and Mission**: Cost-effective enterprise-level general workhorse, supporting tool calls, plug-ins, and RAG processes.
- **Price/performance analysis**: ¥0.00080 /1k input, ¥0.00320 /1k output, providing professional-level features at a price close to free.

#### ERNIE 4.5

- **Positioning and Mission**: Chinese multimodal flagship, good at image + text, long document understanding, and cultural context analysis.
- **Cost-effectiveness analysis**: ¥0.00400/1k input, ¥0.01600/1k output, providing leading results for core Chinese scenarios.

---

### Tencent Cloud Hunyuan Series

#### Hunyuan-lite

- **Positioning and Mission**: Permanently free long context, suitable for PoC, education and large-scale basic services.
- **Cost-Effectiveness Analysis**: ¥0.00000 /1k, extremely cost-effective; but the reasoning depth is not as good as the flagship version.

#### Hunyuan-TurboS

- **Positioning and Mission**: Flagship with trillion parameters, high-concurrency intelligent question-answering and document parsing.
- **Cost-effectiveness analysis**: 1 million tokens are free in the first month, ¥0.00080/1k input, ¥0.00200/1k output, taking into account both cost and performance.

#### Hunyuan-T1

- **Positioning and tasks**: General main model, oriented to complex conversations, full document understanding, and intelligent recommendations.
- **Cost-effectiveness analysis**: ¥0.00100 /1k input, ¥0.00400 /1k output, it is the "economic flagship" of the Hunyuan series.

---

Mistral AI Series

#### Mistral Small 3.1

- **Location and Task**: A lightweight multilingual assistant suitable for basic tasks such as translation, summarization, and classification.
- **Cost-effectiveness analysis**: ¥0.00073 /1k input, ¥0.00218 /1k output, the startup cost is extremely low.

#### Mistral Medium 3

- **Position and Task**: Coding and STEM domain expert, often used in technical documentation generation and analysis.
- **Performance-price ratio analysis**: ¥0.00290 /1k input, ¥0.01450 /1k output, the performance is close to the flagship but the price is better.

#### Mistral Large 2

- **Localization and Tasks**: Open source flagship contender, suitable for the most demanding multimodal and complex reasoning tasks.
- **Cost-effectiveness analysis**: ¥0.02900 /1k input, ¥0.08700 /1k output, providing a free alternative for teams that need top-notch capabilities.

---

### Cohere Series

#### Command R7B

- **Positioning & Mission**: Lightweight RAG prototype build, lowest cost test model.
- **Price/performance analysis**: ¥0.00027 /1k input, ¥0.00109 /1k output, an ideal choice for building RAG PoC.

#### Command R

- **Positioning and tasks**: General enterprise-level RAG, suitable for knowledge base question answering and intelligent search.
- **Cost-effectiveness analysis**: ¥0.00109/1k input, ¥0.00435/1k output, balancing performance and cost.

#### Command A

- **Location and Task**: Dedicated to Agentic AI, supporting multi-step tool calls and complex business processes.
- **Cost-effectiveness analysis**: ¥0.01813/1k input, ¥0.07250/1k output, providing exclusive optimization for complex Agent processes.

---

### Volcengine

#### Doubao-pro-32k

- **Positioning and Mission**: C-end large-scale content generation engine, suitable for social, recommendation, and creation platforms.
- **Cost-effectiveness analysis**: ¥0.00080/1k input, ¥0.00200/1k output, achieving extremely low cost under large traffic.

---

### OpenRouter third-party aggregation platform

#### Llama 3.3 70B（OpenRouter）

- **Positioning and Mission**: Open source flagship "one-click trial", no need to deploy by yourself.
- **Cost-effectiveness analysis**: ¥0.00051/1k input, ¥0.00181/1k output, with convenience as the core value, suitable for PoC and small-scale experiments.

#### 5.1.3 Detailed description

- **Cost Model**

- Billing is based on input/output token usage, without the need for upfront infrastructure investment.
- In the early stage, when the call volume is low, the cost is negligible (free quota can be used); as the call volume increases linearly, the cost rises rapidly.
- Cache input pricing and volume discounts: Many providers offer significant discounts for cache input and batch processing, which can effectively reduce the cost of repetitive tasks. For example, Alibaba Cloud Qwen series can halve the batch processing fee, and cache tokens are charged at 40% of the input cost. DeepSeek's cache hit price is much lower than the cache miss price.
- If the monthly call volume reaches hundreds of millions or more, you need to evaluate the turning point of API cost and self-hosting cost in advance.

- **Online speed and deployment complexity**

- Simply apply for a key to call, easy integration; no need to worry about underlying model deployment, operation and maintenance, capacity expansion, etc., the service provider is responsible for high availability.
- Suitable for quick verification of scenarios and iterative prompts, saving team human resources.

- **Function support (RAG/Agent/Embedding)**

- Basic text/dialogue generation and Embedding interfaces: All mainstream APIs are provided.
- Function Calling: Supports multiple model services, allowing LLM to interact with external systems and data.
- Built-in tools: Some service providers provide tools such as code interpreters, file searches, and web searches.
- RAG support: Developers need to integrate the vector database by themselves or with the help of the framework to implement RAG; some platforms have optimized RAG.
- Multimodal capabilities: Multiple flagship models support image, audio, and video processing.

- **Free Quota**

- International vendors: The free quota is limited and mostly depends on startups or project applications; there are rate/usage restrictions. Platforms such as DeepSeek provide daily free message quotas.
- Domestic manufacturers: often have free or low-price strategies, such as some free models and free token quotas.

- **Compliance**

- Cross-border data and regulatory risks: International APIs pose risks in the domestic production environment and should not be directly used for formal services for domestic users.
- Domestic compliance: Domestic APIs have completed algorithm filing and built-in review mechanisms, and data is stored domestically, making them suitable for use in the Chinese market. If processing highly sensitive data, it is necessary to assess whether private deployment or additional security measures are required.
- Data usage policy: Most providers state that customer data will not be used to train their underlying models.

- **Model Value and Evaluation**

- General Intelligence: Several flagship models lead in general benchmarks. DeepSeek-V3 performs well in relevant tests.
- Chinese processing: Some Chinese models perform well in Chinese understanding and reasoning, especially in multiple benchmark tests.
- Encoding capabilities: Several models performed well on encoding benchmarks.
- Multimodal capabilities: Several flagship models have powerful image, audio, and video processing capabilities.
- Long context understanding: Many models support context windows of millions or even tens of millions of tokens, which is suitable for processing very long documents.
- Cost-effectiveness: Some low-priced or free models offer near-flagship performance, making them ideal for cost-sensitive scenarios.

- **Typical scenario**

- Innovative products, internal tools, research projects for overseas markets; or early rapid demonstration and verification.
- RAG scenarios can be combined with their own vector libraries; if the scale and compliance requirements increase in the future, alternative paths need to be planned in advance.

---

### 5.2. Cloud vendor hosted inference

#### 5.2 Comparison of Hosted Inference Services

##### 5.2.1 Cloud Platform Comparison Overview

| Cloud Platform            | Support Model                                                                                                  | RAG / Agent Ecosystem                                                                                                                                                                   | Billing Model (including other major cost points)                                                                                                                                                                                                                                                                                                                                                                                                     |
| :------------------------ | :------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Azure OpenAI**          | GPT-4o, GPT-4.1 series, o series (o3 / o4-mini)                                                                | Supports MCP protocol integration; newly added image generation and Code Interpreter tools; can call Azure AI Search, Functions and other services to build complex Agents              | **Token billing**: o3 input 2 USD / million tokens, output 8 USD / million tokens; cache input 0.5 USD / million tokens <br> **PTU reservation**: pre-purchase computing resources by instance type <br> **Other fees**: may involve **Azure AI Search (retrieval enhancement)**, **Azure Functions (Agent tool)**, **storage**, **network outbound traffic**, etc.                                                                                   |
| **AWS Bedrock**           | Claude 3, Llama 3, Titan, Mistral AI, Cohere, Stability AI; Claude Opus 4 / Sonnet 4                           | Bedrock Agents support complex multi-step tasks; Claude 4 series can handle 200K token contexts and support "extended thinking" reasoning mode                                          | **Serverless by token**: Claude Opus 4 input 15 USD / million tokens, output 75 USD / million tokens; Sonnet 4 input 3 USD / million tokens, output 15 USD / million tokens <br> **Provisioned throughput**: pre-order discount packages based on API call volume <br> **Other fees**: may involve **Bedrock Agents (coordinator)**, **Amazon OpenSearch (retrieval)**, **Lambda (Agent tool)**, **S3 (storage)**, **network outbound traffic**, etc. |
| **GCP Vertex AI**         | Gemini 1.5 Pro (1 million token context, expanded to 2 million tokens later in 2025), Mistral, Llama 3.1 / 3.2 | Added multi-agent development kit (agent development kit, market, engine) and compatible with MCP protocol; Vertex AI RAG Engine supports long text analysis and multimodal interaction | **Token / GPU hourly hybrid**: Gemini 1.5 Pro input 1.25–2.5 USD / million tokens, output 10–15 USD / million tokens; GPU instances are billed by the hour (A100 is about 0.6 USD / h) <br> **Other fees**: may involve **Vertex AI RAG Engine (retrieval)**, **Cloud Functions (Agent tool)**, **Cloud Storage (storage)**, **network outbound traffic**, etc.                                                                                       |
| **Alibaba Cloud Bailian** | Tongyi Series (Qwen-Long / Max / Plus / Turbo / VL), Llama 3                                                   | Full life cycle MCP service: quickly build Agent in 5 minutes; integrate DashVector vector library, PAI-Lingjun development tools and visual workflow                                   | **Token billing**: Qwen-Long input 0.0005 yuan / thousand tokens, output 0.002 yuan / thousand tokens; Qwen-Max input 0.04 yuan / thousand tokens <br> **GPU instance hour**: V100 about 1.5 yuan / h <br> **Other fees**: may involve **DashVector (vector library)**, **Function Compute (Agent tool)**, **OSS (storage)**, **network outbound traffic**, etc.                                                                                      |
| **Baidu Qianfan**         | Wenxin series (ERNIE 4.5 / X1 / Speed ​​/ Lite), third-party models (such as DeepSeek)                         | AppBuilder low-code development Agent; vector library integrated hybrid retrieval strategy; AI Studio provides full-process tools for model training and deployment                     | **Token billing**: ERNIE X1 input 0.002 yuan/thousand tokens, output 0.008 yuan/thousand tokens; ERNIE 4.5 input 0.004 yuan/thousand tokens, output 0.016 yuan/thousand tokens <br> **GPU instance hour**: A10 about 0.8 yuan/h <br> **Other fees**: may involve **vector database**, **function computing**, **object storage**, **network outbound traffic**, etc.                                                                                  |
| **HUAWEI CLOUD**          | Pangu Series (3.0, industrial fault prediction accuracy > 95%)                                                 | HUAWEI CLOUD CBS supports the construction of industry knowledge graphs; AIUI general semantic model provides basic reasoning; advanced RAG tools are not yet open                      | **Token billing** (reference): Pangu 3.0 input 0.01 yuan/thousand tokens, output 0.04 yuan/thousand tokens <br> **Other fees**: may involve **knowledge graph services**, **cloud functions**, **object storage**, **network outbound traffic**, etc.                                                                                                                                                                                                 |

---

### 5.2.2 Detailed Analysis

#### Price Trends and Core Cost Structure

- **Significant price reduction**: Azure o3, Alibaba Cloud Qwen-Long, AWS Sonnet 4, etc. all hit record low Token prices, reflecting the general downward trend in AI reasoning costs.
- **Diversity of billing models**: Common ones include **Billing by Token** (charged by the actual number of input/output words), **Billing by Instance Hour** (for GPU, self-deployment or training), and **Pre-provisioned throughput/reserved mode** (pre-purchased capacity enjoys discounts), which can meet the needs of different scales and business scenarios.
- **TCO consideration**: The total cost of ownership is not limited to the model call fee. After integrating operation and maintenance, monitoring, network and security services, the one-stop service of the cloud platform can often reduce manpower and complexity, making the overall TCO lower than self-built or self-managed clusters.

#### Ecological and functional evolution

- **RAG / Agent ecosystem mature**: Major cloud platforms have improved the RAG (search enhancement generation) and Agent (agent) ecosystems. For example, Azure MCP, GCP Multi-Agent Development Kit, Alibaba Cloud Bailian MCP, etc., have simplified search enhancement, tool calling, and workflow orchestration.
- **Multimodality and long context**: High-end models (such as Gemini 1.5 Pro supporting millions of tokens, Amazon Nova Premier) seize the "long context + multimodality" market, and can handle more complex inputs and generate richer responses.

#### Industry customization capabilities

- Cloud service providers provide models and solutions optimized for the industry. For example, Huawei Cloud Pangu 3.0 focuses on fault prediction in the manufacturing industry, and Baidu ERNIE X1 emphasizes logical reasoning and multi-step automation. Enterprises can choose AI services with higher matching degree according to industry needs to improve application effects.

#### Speed ​​of launch and complexity of operation and maintenance

- **Quick launch**: The cloud platform console, sample images, and templates enable the creation of AI endpoints in minutes, accelerating development and verification.
- **Cloud-native MLOps**: Monitoring, grayscale release, A/B testing, version management and other functions are commonly built-in, significantly reducing DevOps complexity and costs.

#### Other cost estimates and analysis

In addition to the basic model inference and dedicated resource costs, the total cost of cloud deployment also needs to consider the costs of the following key components. These "hidden costs" may accumulate to exceed the inference costs themselves in complex scenarios or high concurrency, and should be fully incorporated into the budget and architecture design.

1. Data storage fees

- **Purpose**: Storage of documents/data for RAG, model files, application logs, user data, etc.
- **Main services**: object storage (such as S3, OSS, Blob Storage), vector database, relational/NoSQL database.
- **Billing model**: Billing is based on storage capacity (GB/month), data transfer volume, and number of requests.
- **Estimate**:

- **Object storage**: For GB-level RAG data, the monthly cost is usually several dollars to tens of dollars (tens to hundreds of RMB); if massive multimedia is stored, the cost will rise sharply.
- **Vector database**: Depending on the vector dimension, index scale and QPS, it may cost tens to hundreds of US dollars (hundreds to thousands of RMB) per month; large-scale enterprise-level deployments can cost thousands of dollars or more.
- **Database instance**: Based on instance specifications, storage, and read/write load, ranging from tens to thousands of dollars per month.

2. **Network transmission fees**

- **Purpose**: Requests flow into the cloud platform, responses flow out, and data is transmitted between services (such as Agent calling external APIs and RAG retrieving vector libraries).
- **Billed by egress**: Ingress is usually free or very low, and cross-region transfers are more expensive.
- **Estimate**:

- The amount of response data for text AI applications is generally not large, with tens to hundreds of GB of outbound traffic per month, and the cost is between a few US dollars and tens of US dollars (tens to hundreds of RMB).
- If it involves multimedia and a large number of users, the size of the data may reach TB level, costing hundreds to thousands of US dollars (several thousand to tens of thousands of RMB).

3. **Calculate service fees (Agent tool calls, custom logic)**

- **Purpose**: Implement Agent tool calls, API integration, data pre-processing/post-processing, user authentication and other custom logic.
- **Main services**: Serverless Functions (Lambda, Azure Functions, Cloud Functions), Lightweight Container Service, VM/Kubernetes.
- **Billing model**: Billing is based on the number of calls, execution time (GB-seconds), and memory configuration; containers/VMs are billed based on instance specifications.
- **Estimate**:

- The cost of simple Agent calls is extremely low (e.g. 0.00000x USD/time). Small and medium-sized applications may generate tens to hundreds of USD (hundreds to thousands of RMB) per month. Large-scale high-concurrency scenarios may generate higher costs; if complex business logic needs to reside on VM/K8s, the cost may range from tens to thousands of USD per month.

4. **Monitoring and logging fees**

- **Purpose**: Collect, store, and analyze AI application performance indicators, error logs, access logs, etc.
- **Main services**: cloud monitoring, log services.
- **Billing model**: Billing is based on log ingestion volume (GB), storage duration (GB/month), and query volume.
- **Estimate**: Generally relatively low, with most apps costing a few dollars to tens of dollars per month (tens to hundreds of RMB).

5. Security and compliance costs

- **Purpose**: Enhance security and meet compliance.
- **Main services**: WAF, KMS, content security review, audit services, etc.
- **Billing model**: Billing is based on a fixed monthly fee, number of requests, and amount of data processed.
- **Estimate**: Basic security services cost tens of dollars per month; if advanced protection or in-depth compliance support is required, it may cost hundreds to thousands of dollars per month.

> **Tip**: Different project stages, data scale, and business complexity determine the proportion of each part of the cost. In the PoC/Beta stage, these "hidden costs" are relatively low and can be verified with free quotas or small-scale deployments; in large-scale production or high-performance scenarios, it is necessary to focus on optimization and monitoring to avoid out-of-control expenses.

#### Free quota and business plan

- **Wide support**: Azure Founders Hub, AWS Activate, Google Startups, Alibaba Cloud Entrepreneur Program, Baidu Qianfan Entrepreneur Program, etc., providing free quotas or discounts.
- **Utilization suggestions**: Use the free quota in the PoC and Beta stages to reduce initial costs; apply for VC/accelerator endorsement to obtain higher quotas; do not rely directly on free quotas in production environments, and leave sufficient budget.

#### Compliance and Security

- **Region and data control**: Choose hosting in the right region to meet data residency and privacy regulations; enable features such as encrypted transmission and zero-trust network.
- **Certification and assurance**: Most mainstream cloud vendors have passed ISO 27001, SOC 2 and other certifications, and can sign additional terms to ensure that data is not used for model training.
- **Custom model considerations**: Deploying your own models requires additional configuration of content security testing and manual review processes; regular audits are required to ensure compliance.

#### Typical application scenarios

- **Beta-level workloads**: Customer service robots, knowledge centers, marketing automation, etc. require rapid deployment and iteration, and can prioritize the cloud hosting model and RAG/Agent integration.
- **High privacy and regulatory requirements**: In scenarios such as finance and healthcare, you can choose domestic regional hosting or privatized endpoints to ensure data isolation and compliance.
- **SaaS multi-tenancy**: SaaS vendors can use the cloud platform to quickly deliver "per-customer, one-tenant" private inference services, improving security and differentiation through isolation and customization.

#### Risks and Response Strategies

- **Vendor lock-in**: Design abstraction layers and unified vector interfaces to facilitate migration between different cloud platforms; avoid deep binding to a proprietary API.
- **Cost out of control**: Enable budget alerts and automatic scaling; introduce quantization, mixed precision, KV cache and other technologies at the inference level to optimize performance and reduce the cost of a single inference; review usage regularly.
- **Compliance Update**: Continue to track changes in AI regulatory policies in various countries, and promptly update sensitive data governance and audit processes; combine the opinions of the legal team to ensure that the application always complies with regulatory requirements.

---

### How to effectively manage the total cost of cloud deployment?

1. **Architecture optimization**: Rationally design the RAG and Agent architecture to reduce unnecessary data transmission and repeated calculations; try to communicate within the cloud platform's internal network.
2. **Data lifecycle management**: Regularly clean up logs and storage data that are no longer needed to avoid the accumulation of long-term storage costs; archive or delete old version models or snapshots that are no longer used.
3. **Service selection**: Give priority to using the cloud platform's built-in services and internal networks to reduce the cost of public network outbound traffic; select the appropriate storage type (such as hot and cold tiering) based on the access mode.
4. **Elastic Scaling**: Enable automatic scaling to ensure that you only pay for the resources you actually use; automatically reduce the instance size during low traffic hours to save costs.
5. **Utilize free quota**: During the PoC and Beta stages, actively apply for and utilize free or discounted quotas from various cloud vendors; avoid over-reliance on free quotas in production environments.
6. **Budget and Alert**: Set detailed budgets, spending limits, and alert policies on the cloud platform; monitor cost indicators in real time, and optimize or adjust resource allocation in a timely manner when the budget approaches the threshold.
7. **Performance optimization**: Introduce technologies such as caching (such as embedding caching), mixed-precision reasoning, and batch processing to improve unit resource utilization and reduce reasoning costs.
8. **Log and monitoring optimization**: Rationally configure log levels and retention periods to avoid excessive log ingestion and storage costs; use sampling or hierarchical storage strategies.
9. **Security and compliance automation**: Use automated tools for security scanning and compliance checks to reduce manual audit costs; configure appropriate access control and audit logs.
10. **Regular review**: Regularly review the deployment architecture and cost structure, and optimize them based on business growth or changes; evaluate newly released cloud services or models to determine whether there are better options.

---

## 5.3 Low-code/scheduling platform and framework

## 5.3.1 Platform and framework comparison (including price information)

| Platform/Framework | Type                                        | Main Features                                                                                   | Typical Users                               | Pricing Model and Latest Price (June 2025)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Pros and Cons Summary                                                                                                                              |
| ------------------ | ------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dify               | Application Platform (SaaS/Self-hosted)     | Visual application orchestration, built-in RAG, Agent, monitoring, multi-model scheduling       | Product Manager, Developer                  | Self-hosted version: core functions are free and open source. <br>Dify Cloud: <br>- Starter: about ￥ 428/month (\$59), including 3 million tokens <br>- Pro: about ￥ 1153/month (\$159), 10 million tokens <br>- Exceeding $0.25/million tokens                                                                                                                                                                                                                                                                                                                                                                | ✅ Strong Chinese support, active ecology, flexible deployment; ❌ Slightly less flexible, complex processes require secondary development         |
| Coze               | Application Platform (SaaS)                 | Multi-model intelligent agent construction, multi-channel publishing, plug-in extension support | Operation, Developer                        | - Free: ￥ 0, 10 credits/day, 5 people collaborating, 3 Bots/workflows, support Skylark-lite, GPT-3.5, Claude 3 Haiku, GPT-4o mini, etc.<br>- Premium Lite: about ￥ 66/month (\$9), 100 credits/day, 10 people collaborating, 10 Bots, support for mainstream models increased<br>- Premium: about ￥ 140/month (\$19), 400 credits/day, 50 people collaborating, 50 Bots, support for more advanced models (GPT-4o 8k/32k, DeepSeek, Gemini Pro, etc.)<br>- Premium Plus: about ￥ 285/month (\$39), 1000 credits/day, 100 people collaborating, Bot Unlimited, first choice for high-frequency call scenarios | ✅ Free entry threshold is low, supports multiple models and plug-in ecosystems;<br>❌ Advanced model calls consume quickly, free quota is limited |
| FastGPT            | RAG Platform (open source self-hosted)      | Knowledge base optimized RAG process, Agent workflow, support API access                        | RAG Developer                               | - Free: ￥ 0, 3 people/30 applications/10 knowledge bases, 30 days retention, 600 indexes, 100 AI points<br>- Experience: ￥ 59/month, 10 people/80 applications/30 knowledge bases, 180 days retention, 5000 indexes, 3000 AI points<br>- Team: ￥ 399/month, 50 people/200 applications/100 knowledge bases, 360 days retention, 40,000 indexes, 20,000 AI points<br>- Enterprise: ￥ 999/month, 500 people/1000 applications/500 knowledge bases, 720 days retention, 150,000 indexes, 60,000 AI points Points                                                                                                | ✅ Free and self-hosted, active ecosystem, supports quick launch;<br>❌ Free version has limited functions, advanced functions require payment     |
| Ragflow            | RAG Platform (open source self-hosted)      | Deep document understanding, long text optimization, complex format support                     | Advanced RAG Developer                      | Completely free open source, no cloud service plan                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | ✅ Deep document parsing, unlimited token processing; ❌ High technical threshold, slightly high deployment cost                                   |
| LangChain          | Development framework (open source library) | Modular construction of complex LLM applications such as RAG, Agent, tool calls, etc.           | Senior developers                           | Free open source, the cost comes from LLM API calls and server resources                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | ✅ Active community, rich ecology; ❌ Steep learning curve, complex state management                                                               |
| LlamaIndex         | Development framework (open source library) | LLM connects to external data, RAG, Agentic RAG                                                 | Developers, researchers                     | Free open source, cost is similar to LangChain                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | ✅ Wide data access and good retrieval performance; ❌ Complex concepts, need to master the framework design concept                               |
| CrewAI             | Agent Framework (Open Source Library)       | Multi-agent collaboration framework, supports RAG and Agent division of labor                   | Senior developers, researchers              | Free open source, running costs are the same as LangChain                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | ✅ Clear abstraction, suitable for team-based agents; ❌ Limited customization, scarce documentation                                               |
| AutoGen            | Agent Framework (open source library)       | Microsoft product, supports multi-agent dialogue, code execution                                | Researchers, scientific research developers | Free open source, running costs are the same as above                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | ✅ Powerful communication model, suitable for scientific research exploration; ❌ Limited tools, cumbersome deployment                             |
| Flowise            | Workflow platform (open source self-hosted) | Visual drag-and-drop process orchestration, support for Agentic RAG, multi-tool integration     | Automation developers                       | Completely free and open source, a commercial version may be launched in the future                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | ✅ User-friendly and rich in components; ❌ Slightly less flexible, complex scenarios still require code support                                   |

#### 5.3.2 Detailed description
---

### Dify detailed function breakdown

- **Visual Application Orchestration**

- Drag-and-drop or low-code UI: Configure the RAG pipeline (document upload → Embedding generation → Vector retrieval → Prompt combination → Model call → Result output) and multi-step Agent workflow through a graphical interface.
- Support conditional branching and looping: You can add conditional judgments in process nodes to implement complex logic (such as routing different sub-processes based on search results).
- Debug panel: You can view the intermediate data of each step (such as Embedding vector dimensions, search result summary, Prompt content) in real time to facilitate problem location.

- **Built-in RAG support**

- Access to multiple vector databases: such as Elasticsearch, Weaviate, Pinecone, Milvus, and FAISS (optional for self-hosting). The cloud version can be directly hosted or connected to existing services.
- Document preprocessing and segmentation: automatic splitting of long texts, support for PDF/Office documents, uploading and parsing of multiple formats (Markdown, TXT, HTML), automatic deduplication and cleaning.
- Embedding generation and tuning: You can configure different Embedding models (OpenAI, open source models, user-owned models), support batch/incremental updates; you can set similarity thresholds, Top-K, filtering strategies, etc.
- Dynamic prompt splicing: supports templated prompts, short-term memory, and historical dialogue injection, making it easier to do conversational question-and-answer or multi-round search enhancement.
- Write-back and result fusion: Supports multi-document retrieval result fusion strategies (based on score weighting, re-ranking, summary merging, etc.), and can backfill the fusion results to Prompt to improve accuracy.

- **Agent Workflow**

- Multi-tool calling: supports calling external APIs (such as database queries, business system interfaces), internal functions (scripts), and even self-hosted microservices; integrates existing systems through HTTP, Webhook, RPC, etc.
- Parallel/serial tasks: Multiple model calls or retrievals can be initiated in parallel in the same process, and the results can be aggregated later; they can also be called serially to form a chain decision.
- Error handling and retry: Exception capture nodes and timeout retry strategies can be defined in the process to ensure system reliability.
- Timing/Trigger: Supports triggering Agent based on time or external events, such as re-indexing after regular data updates and automatically triggering the retrieval process when new documents arrive.

- **Multi-model scheduling and management**

- Model Registry: Supports connecting to multiple cloud vendors or self-hosted model services (OpenAI, Azure OpenAI, Anthropic, locally deployed LLaMA series, etc.), and managing them in the same interface or code.
- Scheduling strategy: Dynamically route requests to different models based on request type or cost budget (e.g., use a small model for quick pre-screening and then use a large model for in-depth answers).
- Load control: high concurrent requests can be limited and queued; the cloud version of the platform will perform elastic scaling in the background according to the subscription level.
- Monitoring and indicators: Provides the time, number of calls, and token consumption of each model call, and supports data export or integration with third-party monitoring systems (such as Prometheus and Datadog).

- **Deployment Flexibility**

- Self-hosted version is free: the source code is open source and can be deployed in a private cloud or local cluster, managing computing resources and security by yourself; it is suitable for scenarios with sensitive data and high compliance requirements.
- Cloud hosting (Dify Cloud): Used on a subscription basis, no hardware maintenance is required, but you need to be concerned about the storage and privacy of data on third-party platforms. The cloud version provides one-click deployment environment, automatic upgrade and backup functions.
- Hybrid mode: You can call cloud services (such as Embedding API or large model inference) in a self-hosted environment, or mount private databases or local APIs in the cloud version.

- **Monitoring and Logging**

- Detailed logs: Request and response logs, error logs, and business logs can all be viewed; log filtering and searching are supported.
- Usage statistics: statistics on call volume, cost consumption, and major bottlenecks by team/project dimensions; support setting alarm thresholds.
- Performance Analysis: Automatically generate performance reports (such as average response time, peak concurrency period) to help optimize architecture and subscription level.

- **Multi-language and localization**

- Excellent Chinese support: built-in Chinese word segmentation, Chinese document parsing and retrieval optimization; Prompt template examples are multi-language compatible.
- Internationalization: The interface supports multiple languages, which can adapt to the multi-language usage scenarios of the team.

- **Typical application scenarios**

- Product prototype verification: Business teams or product managers can quickly build prototypes such as knowledge quizzes, intelligent customer service, and automatic report generation.
- Internal tools: HR, legal affairs, and R&D team internal knowledge base retrieval and automation processes (such as automatic generation of meeting minutes and document proofreading).
- Small and medium-sized online services: External services can be integrated into the official website or App and called through the SDK/HTTP interface.
- Scenarios with high compliance requirements: The self-hosted version meets strict requirements for data privacy or legal compliance (such as the medical and financial industries).

- **Threshold and cost**

- Self-hosting requires strong operation and maintenance capabilities: you need to prepare servers, container orchestration (such as Kubernetes), databases (vector storage), monitoring systems, etc.
- Cloud version subscription cost: Starter (￥ 428/month) is suitable for light testing; Pro (￥ 1153/month) is suitable for small and medium-sized teams; advanced usage requires evaluation of the excess call costs.
- Team size and usage frequency: If the daily call volume or Embedding updates are frequent, you need to make cost forecasts in advance or choose a flexible solution (self-hosted + on-demand cloud API).

---

### Coze detailed function breakdown

- **SaaS model and point-based billing**

- Basic free quota: 10 credits per day, which can be used to try out mainstream small/medium models (Skylark-lite, GPT-3.5, Claude 3 Haiku, GPT-4o mini, etc.), suitable for lightweight testing by individuals or small teams.
- Credits consumption logic: Different models and plug-ins (such as WebPilot, Stable Diffusion, DALL·E3, etc.) consume different credits. The document lists the consumption of each model per call and the estimated daily call limit to facilitate budget planning.

- **Bot/Workflow Build**

- Visual or code-based orchestration: Provides a graphical process editor, allows the introduction of custom scripts or function nodes, and integrates with external systems through Webhook/API.
- Multi-channel publishing: supports publishing Bot to multiple terminals such as WeChat, Slack, Telegram, web page embedding, etc.; built-in OAuth, Webhook and other docking methods make access more convenient.
- Collaboration mechanism: Team members can jointly edit and manage Bots, and permission management is relatively basic (collaboration quota depends on subscription level).

- **Multiple model support and scheduling**

- Built-in multiple models: from lightweight Skylark-lite to GPT-4o with different context windows, different consumption and capabilities; multiple models can be combined in the same workflow (such as using a small model for preprocessing first, and then using a large model for deep answering).
- External model access: Supports binding of users' own model API keys (such as OpenAI, Anthropic, Azure OpenAI, etc.). Calls are still charged by Coze credits, or direct connection can be considered in premium subscriptions (platform policy needs to be confirmed).
- Plugin ecosystem: supports common plugins (search, image generation, data crawling, etc.). Calling plugins also consumes credits. Customizable plugin access is available.

- **Monitoring and Analysis**

- Usage statistics: Display daily/monthly call volume, credits consumption details, and each Bot performance indicator (response time, error rate); support exporting reports for cost analysis.
- Log query: You can view detailed logs of a single conversation or Workflow execution, including request parameters, model response, and exception information; this helps troubleshoot logic or prompt issues.
- Alarms and current limiting: You can set a call limit or alarm threshold for key bots to avoid excessive consumption caused by misuse; the higher the subscription level, the richer the configuration options.

- **Team and authority management**

- Number of collaborators: The number of collaborators is limited according to the subscription level; basic role divisions (administrators, editors, etc.) are supported, but the permission granularity is relatively simple.
- Organization/project isolation: multiple projects or workspaces can be managed to avoid interference between different business lines; cost centers can be isolated to facilitate financial accounting.

- **Integration and Extension**

- External system connection: Support integration with internal enterprise systems (CRM, ERP, database) through Webhook, API Key, etc. to realize automated business processes.
- Custom scripts: Custom JavaScript or other scripts (depending on platform support) can be embedded in the Workflow to handle complex business logic.
- Plug-in market: Some common functions (such as search engines, image generation, and file parsing) already have built-in plug-ins, which reduces the cost of secondary development; when custom plug-ins are needed for advanced scenarios, certain development investment is required.

- **Deployment and Maintenance**

- SaaS is ready to use: there is no need to operate and maintain the environment by yourself, the platform is responsible for availability, scaling, and security updates; it is suitable for rapid online launch, pilot projects, or teams with limited operation and maintenance resources.
- Data privacy: All conversations and documents are stored in the Coze cloud, and privacy and compliance risks need to be assessed; if sensitive data is involved, you should communicate with the platform or choose a self-hosted/private deployment solution (if any).
- Backup and recovery: The platform provides basic backup mechanisms, but they may not meet strict legal compliance (SLA details need to be confirmed).

- **Multi-language and localization**

- Interface/document multi-language support: The interface is usually available in Chinese/English, with a low operating threshold; prompt templates or examples contain Chinese and English versions, which is convenient for domestic teams to use.
- Model effect: Good support for Chinese text, free or low-level models are sufficient for simple question-answering; high-level models are recommended for complex business scenarios, but credits consumption and costs need to be evaluated.

- **Typical application scenarios**

- Lightweight prototype: quickly verify Bot ideas, internal Q&A, or customer service demo.
- Automation for small and medium-sized teams: internal knowledge base Q&A, process automation (such as automatic replies, simple data queries).
- Educational or personal projects: Learn and try out multi-model capabilities without heavy asset investments.
- Be cautious in highly sensitive scenarios: For scenarios with high requirements for data privacy, such as finance and medical care, additional risk assessment is required if there is no private deployment option.

- **Decision-making recommendations**

- If your team has limited operation and maintenance resources, needs to go online quickly, and the data sensitivity is not high, you can choose Coze SaaS.
- If the call volume is high and the cost is sensitive, you should calculate the credits consumption and compare it with self-hosting or other subscription models.
- If you need more flexible customization or have high compliance requirements, you can consider evaluating open source self-hosting solutions (such as Dify self-hosting or LangChain frameworks).

---

### FastGPT detailed function analysis

- **Core Positioning**

- Open source self-hosted RAG platform, emphasizing knowledge base optimization and agent workflow; while providing cloud hosting subscriptions to lower the deployment threshold.

- **RAG pipeline**

- Document processing: supports parsing and preprocessing of multiple formats (PDF, Office, Markdown, HTML, etc.); automatic segmentation, deduplication, and cleaning functions.
- Embedding management: multiple embedding models can be configured (self-hosted or cloud API), support incremental updates and batch indexing; provide an index management interface.
- Vector search optimization: supports multiple index types (HNSW, IVF+PQ, etc.); adjustable recall parameters to meet the needs of long text and high concurrency scenarios.
- Prompt splicing and multi-round dialogue: Supports conversational RAG with context memory; configurable historical dialogue injection strategy to prevent context expansion.

- **Agent and plugins**

- Process orchestration: Define multi-step processes through YAML/JSON or Web UI, support calling external APIs, executing custom scripts, or triggering internal functions.
- Extension interface: SDK (Python/Node.js, etc.) is provided to facilitate embedding RAG services in existing systems; it can also be directly called through RESTful API.
- Plug-in mechanism: You can write custom plug-ins to extend functions, such as customized data source access and business system docking; the community-contributed plug-in ecosystem is gradually enriched.

- **Deployment and Operation**

- Self-hosted and free: can be deployed in Kubernetes or Docker Compose environment, supports elastic scaling; the team is required to have operation and maintenance capabilities (network, storage, security configuration, etc.).
- Cloud version subscription: From Free to Enterprise, you can quickly obtain a hosting environment without having to worry about the underlying operation and maintenance; however, you need to evaluate data privacy.
- Monitoring integration: When self-hosted, it can be integrated with monitoring systems such as Prometheus and Grafana; the cloud version has built-in basic monitoring and alarm configuration.
- Automated operation and maintenance: supports CI/CD pipeline access (such as GitOps) to facilitate continuous iteration and grayscale release; high subscription levels may provide platform-level backup and SLA support.

- **Multiple Model Management**

- Model registration: supports connecting to external large model APIs (OpenAI, Azure, Anthropic, locally deployed LLM); flexible request routing.
- Intelligent Scheduling: Dynamically select models based on request characteristics or cost budget; support downgrade strategy (use small models when large models are unavailable or exceed budget).
- Version management: multiple versions of prompt templates or processes can be managed and rollback is supported.

- **SECURITY AND COMPLIANCE**

- Self-hosted environment: Users have full control over data storage, transmission encryption, etc., which can meet high compliance scenarios; users need to configure TLS, access control, identity authentication, etc. by themselves.
- Cloud version security: The platform provides basic encryption and access mechanisms, but compliance requirements such as data retention period and physical location need to be confirmed; it supports enterprise version SLA and dedicated network isolation (if any).
- Audit log: records call logs and user operation logs to facilitate post-audit and problem troubleshooting.

- **Multi-language support**

- Interface and documentation: multi-language (at least Chinese and English) support; community or commercial versions provide more localized examples.
- Multilingual search: built-in Chinese search optimization, word segmentation and similarity tuning; also supports English or multilingual documents.

- **Scalability and performance**

- Horizontal expansion: It can be expanded horizontally through container or service cluster deployment; the index layer supports sharding or distributed configuration to cope with large-scale knowledge bases.
- Concurrency: Self-hosting requires you to tune your own resources (CPU/GPU/memory); the cloud version will automatically adjust or prompt for upgrades based on your subscription.
- Performance indicators: provide query response time, throughput, and background task (such as Embedding update) monitoring; help optimize hardware configuration and subscription selection.

- **Typical scenario**

- Internal knowledge platform for medium and large enterprises: self-hosting meets compliance requirements, and cloud hosting ensures rapid launch.
- R&D tool chain integration: Embed IDE and DevOps platforms through SDK/API to achieve intelligent document retrieval and code assistance.
- Support for multiple business lines: You can create independent databases for different teams (HR, legal affairs, R&D, customer service) and configure different permissions.

- **Decision-making recommendations**

- If you need high customization, deep integration, and compliance control, and your team has operation and maintenance capabilities, self-hosted FastGPT is a good choice.
- If you want to go online quickly and iterate gradually, you can start with a low-level subscription of the cloud version, and then evaluate self-hosted or higher subscriptions.
- Pay attention to costs: For large-scale indexing or high-concurrency retrieval scenarios, you need to plan resources or subscribe to slots in advance to avoid sudden cost increases later.

---

### Ragflow detailed function breakdown

- **Core Positioning**

- Focuses on deep document understanding and long text optimization, supports the processing of extremely large amounts of tokens, is not limited by traditional short text segmentation, and is suitable for processing extremely large documents or multi-document fusion scenarios.

- **Document parsing and understanding**

- Intelligent segmentation strategy: not only simply split by fixed length, but also split based on semantic structure (chapter, paragraph, sentence); support custom segmentation rules.
- Long text aggregation: Segmented aggregation retrieval can be performed on very long texts, using hierarchical retrieval (rough search first, then fine search) or layered summarization to reduce the amount of calculation while ensuring semantic integrity.
- Complex format support: Better parsing capabilities for complex document formats with tables, formulas, diagrams, etc.; structured information can be extracted for subsequent logic or data processing.

- **Vector storage and retrieval**

- Unlimited Token Processing: No need to manually split small fragments, very large contexts can be processed at one time, and repeated calculations can be reduced through unique indexing and retrieval algorithms.
- Vectorization strategy: supports access to multiple Embedding models, customized similarity calculation, and weighted retrieval; in a self-hosted environment, the underlying index parameters can be tuned to adapt to large-scale corpora.
- Retrieval tuning: Provides refined recall control, such as multi-stage retrieval, result fusion, and dynamic thresholds; suitable for professional scenarios with extremely high precision requirements (legal texts, scientific research documents, and large white papers).

- **Deployment complexity**

- Mainly self-hosted: Currently, open source versions are mainly used, with no cloud hosting services (or not yet publicly available); deployment requires deep infrastructure configuration (high-performance computing nodes, distributed storage, memory and disk optimization).
- High resource requirements: Large-scale document processing and deep semantic understanding have high requirements for CPU/GPU, memory, and disk IO, and require the team to have mature operation and optimization capabilities.
- Clusterable: Supports distributed deployment, distributing indexing and retrieval loads to multiple nodes; cluster communication, load balancing, and fault recovery need to be configured by yourself.

- **Integration capabilities**

- API/SDK: Provides a calling interface for easy integration into existing systems; however, there may be relatively few examples and documents, requiring developers to read the source code or community examples in depth.
- Compatible with common vector libraries: can be connected to mainstream vector databases or come with optimized indexes; needs to be built and maintained by yourself.
- Compatible with other frameworks: It can be used as a backend retrieval component in frameworks such as LangChain and LlamaIndex, but the integration work requires users to adapt it themselves.

- **Monitoring and Tuning**

- Self-hosted monitoring: You need to build your own monitoring solution (such as Prometheus + Grafana) to monitor resource usage, response time, index update progress, etc. in real time.
- Tuning tools: provide some command lines or management interfaces to adjust search parameters and index refresh strategies; specific optimization requires continuous experimentation based on business scenarios.

- **SECURITY AND COMPLIANCE**

- Full data control: Under self-hosting, data is fully under control, but encryption, access control, audit logs, etc. need to be implemented by the team; the team needs to have relevant security capabilities.
- Compliance and applicability: Suitable for internal deployment of ultra-large-scale professional documents (such as legal and regulatory libraries, scientific research literature libraries); if public cloud hosting is available, the security qualifications of the cloud provider can be evaluated.

- **Typical scenario**

- Scenarios such as law, finance, and government that require deep retrieval and reasoning of large-scale documents.
- Research institutions need to perform aggregate analysis or automatic writing assistance across massive amounts of literature.
- Scenarios that require "processing a large document at once" rather than "segmented and spliced ​​multiple times" to avoid misunderstandings caused by context fragmentation.

- **Decision-making recommendations**

- If the team has sufficient operation and maintenance and hardware resources, and has extremely high requirements for in-depth understanding of long texts, Ragflow self-hosting can be given priority.
- Not suitable for lightweight scenarios or teams with limited operation and maintenance capabilities; it can be combined with other lightweight RAG platforms for verification in the small-scale or prototype stage, and then Ragflow can be evaluated for in-depth requirements.
- Can be used in conjunction with FastGPT/other frameworks: Use a lightweight platform for regular document scenarios, and use Ragflow for in-depth processing in critical ultra-large document scenarios, and then summarize the results.

---

### LangChain detailed function analysis

- **Positioning and Features**

- An open source framework library that provides modular components to quickly build complex LLM applications such as RAG, Agent, and multi-tool calls; highly flexible and with a rich community ecosystem.

- **Core Components**

- LLM interface abstraction: Unify the connection to different large model APIs (OpenAI, Azure, Anthropic, self-hosted LLM, etc.), encapsulate the calling method, and facilitate switching.
- Prompt templates and filling: support Jinja, templated prompt management, easy reuse and version control; support dynamic interpolation and conditional logic embedding.
- Chain construction: Chain is formed by connecting multiple steps (LLM call, data processing, condition judgment, etc.); parallel execution and asynchronous call are also supported.
- Memory management: Provides short-term/long-term memory interfaces that can be used for conversation history preservation and state management; can be combined with external storage such as Redis.
- Agent mode: supports zero-sample, few-sample, and tool-based agents, automatically selects tools or prompts users; built-in tool manager, customizable tools.
- Document retrieval integration: compatible with various vector databases such as LlamaIndex, Chroma, Pinecone, FAISS, Weaviate, etc.; supports Embedding generation, segmentation strategy, and custom retrieval logic.
- Callback mechanism: You can insert hooks to monitor each step of the call, log, debug or make dynamic adjustments; it is convenient to observe intermediate output and statistical indicators during development.

- **Expanding the Ecosystem**

- Third-party integration: The community contributes a large number of examples and extension modules, such as seamless integration with databases (SQL, NoSQL), search engines, crawlers, message queues, cloud services, etc.
- Custom components: You can customize Chain, Agent, Tools, Memory, and Callback to meet special business needs.
- Templates and Examples: The official and community documents provide a wealth of examples, but they require reading and understanding, and the learning curve is relatively steep.

- **Deployment and Operation**

- There is no official hosting, and users need to deploy it on their own infrastructure or cloud; there is a high degree of freedom in deployment methods, and it can be combined with containers, Serverless, cloud functions, etc.
- Dependencies and versions need to be managed: The LangChain version and related dependencies need to be locked in the project, and forward compatibility needs to be paid attention to during regular upgrades.
- Monitoring and logging: You need to integrate monitoring (such as Prometheus) and logging systems (such as ELK) to collect runtime metrics and link tracking.
- Extended concurrency: Multiple instances or stateless services can be horizontally extended and automatically scaled according to load; concurrency control and rate limiting need to be considered.

- **SECURITY AND COMPLIANCE**

- Data storage and privacy: It is completely under the control of the user, and a private environment can be used for sensitive data; the proxy mode can perform encryption and desensitization before and after calling external APIs.
- Access control: Implement authentication and authorization mechanisms on your own, such as adding a gateway or API Token access to internal services; additional development work is required.
- Audit: Detailed call logs can be recorded in Callback for auditing and tracing.

- **Difficulty and team requirements**

- Suitable for experienced developers or R&D teams who are familiar with Python ecosystem, asynchronous programming, microservice architecture, etc.
- Steep learning curve: You need to understand concepts such as Chain, Agent, Callback, etc.; it may take time to build the basic framework in the early stages of the project.
- High flexibility: It can provide sufficient capabilities when the business complexity is high, but it is relatively cumbersome and the input-output ratio needs to be evaluated.

- **Typical scenario**

- Automation of complex business processes: multiple system calls, multi-step reasoning, and a large number of conditional judgment scenarios.
- Custom requirements: Connecting to special internal systems may require strict control of call logic and require high degree of customization.
- R&D or experimentation: New ideas and new agent strategies need to be quickly iterated, debugged and verified in a controllable environment.

- **Decision-making recommendations**

- If the team has strong development capabilities and requires high customization, LangChain is the preferred open source framework; however, sufficient development and maintenance costs must be reserved.
- If you want to quickly verify simple scenarios, you can use higher-level platform integration (such as Dify, Coze), and then introduce LangChain to deepen customization after the demand matures.
- For sensitive data, LangChain self-custody can combine desensitization and encryption methods to meet compliance requirements.

---

### LlamaIndex detailed function breakdown

- **Positioning and Features**

- Focus on data access and RAG: quickly connect external data sources (files, databases, web crawlers, etc.) to LLM for retrieval enhancement tasks; can be used in conjunction with frameworks such as LangChain.

- **Core Components**

- Data Loader: Built-in multiple file format loaders (PDF, Word, Markdown, JSON, CSV, etc.) and database connectors (SQL, NoSQL), and you can customize Loader to implement special data sources.
- Document sharding and index building: Provides flexible sharding strategies (fixed length, semantic paragraph, title segmentation, etc.), and supports multiple index types (tree index, list index, vector index, etc.).
- Embedding management: Multiple embedding models can be configured and batch or incremental indexing is supported; there are optimization mechanisms for large-scale data sets, such as batch building, concurrent indexing, caching, etc.
- Query interface: Provides high-level API for query, automatically splices prompts, and injects search results into LLM calls; supports retaining context during multiple rounds of conversations.
- Pluggable backends: supports vector backends such as Pinecone, Chroma, FAISS, Weaviate, Milvus, etc.; also supports simple memory indexing for fast prototyping.

- **Integration and Extension**

- Combined with LangChain: The query results of LlamaIndex can be used as a part of LangChain Chain to achieve more complex processes.
- Custom indexing and search strategies: Custom sorting, filtering or multi-stage retrieval (rough search first, then fine search) can be implemented; results can be fused or weighted.
- You can insert custom prompt construction logic, such as dynamically generating different prompts based on search results, and you can also debug in Callback.

- **Deployment and Maintenance**

- Fully open source and self-hosted: relies only on user-provided model services and computing resources; no cloud-hosted version (or community-provided hosting services).
- Performance and resources: Memory and disk must be allocated properly for large-scale indexing and retrieval, and external storage and cluster support may be required; it is very friendly to small and medium-sized knowledge bases.
- Monitoring: You need to build your own monitoring and logging system to track index building progress, query response time, resource usage, etc.

- **SECURITY AND COMPLIANCE**

- Full data control: Users manage their own data sources to meet compliance requirements; desensitization and encryption can be performed during data loading.
- Access control: Permission control can be implemented in upper-level applications. LlamaIndex itself does not contain a user management module and requires additional development.

- **Difficulty of use**

- Suitable for developers or researchers: You need to be familiar with Python and understand the basic principles of RAG; it is easier to get started than LangChain, but deep customization still requires some experience.
- Rapid prototyping: For common document retrieval scenarios, it can be implemented quickly; for complex business logic, it needs to be combined with other frameworks or custom codes.

- **Typical scenario**

- Knowledge base Q&A, document summarization, report generation: quickly connect existing documents to LLM.
- Research prototype: You need to try different indexing strategies and backend storage, compare the effects and optimize.
- Small team or POC: Can run lightly self-hosted or in conjunction with a small cloud instance.

- **Decision-making recommendations**

- If you are mainly concerned with data access and RAG basic functions and want to complete the prototype quickly, LlamaIndex is the first choice.
- If the business has more complex processes, it is recommended to combine LangChain or other frameworks and use LlamaIndex as a retrieval component.
- For ultra-large-scale scenarios or scenarios with extremely high performance requirements, it is necessary to combine distributed storage or professional vector databases and make good resource planning.

---

### CrewAI detailed function breakdown

- **Positioning and Features**

- Multi-agent collaboration framework, focusing on the division of labor and collaboration among multiple agents; suitable for scenarios where multiple roles or modules need to collaborate to complete a task.

- **Core Components**

- Agent definition and management: You can define different types of agents (such as retrieval agents, decision agents, execution agents, etc.), and configure their capabilities, permissions, and communication interfaces.
- Collaboration Protocol: Built-in or customizable inter-agent communication protocol that supports message passing, event subscription, and asynchronous task scheduling.
- RAG and tool calls: A single Agent can be embedded in a RAG chat or call external tools, and multiple Agents can be combined to complete more complex tasks (e.g. one Agent is responsible for retrieval, one for analysis, and one for execution).
- State management: The framework manages the state of each agent and can persistently store conversation context and temporary data; it supports backtracking and fault recovery.
- Extensible plug-ins: Supports adding plug-ins or extension modules to Agent, such as domain-specific knowledge modules, external system interface modules, etc.

- **Deployment and Operation**

- Self-hosted: Completely open source, users need to deploy it on the server or container by themselves, manage Agent instances, message buses or queues (such as RabbitMQ, Kafka).
- Resource management: It can be horizontally expanded or distributed according to the number of agents and task complexity; communication middleware, resource isolation and monitoring need to be configured.
- Monitoring and logging: You need to integrate your own monitoring system to track the performance of each agent, message queue status, error log, etc. The framework may provide a basic logging interface.

- **SECURITY AND COMPLIANCE**

- Permission control: Different permissions can be assigned to different Agents (such as accessing specific data sources or performing specific operations), but developers are required to implement fine-grained security policies.
- Data isolation: Multiple agents may share or isolate data. Data flow and storage strategies need to be designed according to the scenario. The framework itself needs to cooperate with the platform security mechanism.

- **Difficulty of use**

- Suitable for senior developers or research teams: experience in distributed systems, asynchronous programming, message queues, etc. is required.
- Learning cost: It is necessary to understand the multi-agent architecture design and concurrent collaboration mode. The initial construction cost is high, but it can bring clearer division of labor in complex scenarios.

- **Typical scenario**

- Complex business automation: requires multiple modules or roles to be divided according to the process, such as financial transaction approval, complex event response, and multi-source data fusion and analysis.
- Enterprise-level system: Different departments or microservices collaborate in the form of agents to form cross-team process automation.
- Research and Experimentation: Explore multi-agent collaboration strategies, social intelligence, or simulation scenarios.

- **Decision-making recommendations**

- If the business scenario itself is clearly modular, requires multiple roles, and the team has the corresponding technical capabilities, CrewAI can significantly clarify responsibilities and processes.
- For simple or small to medium-sized scenarios, it may be more efficient to use a single agent or a lightweight framework. You can first use LangChain, etc., and then evaluate whether multi-agent collaboration is needed.
- The operation and maintenance costs are high, and the benefits and development investment need to be evaluated.

---

### AutoGen detailed function breakdown

- **Positioning and Features**

- A multi-agent dialogue and collaboration framework launched by Microsoft, emphasizing dialogue between models, code execution, and tool calling; it is aimed at scientific research or internal large-scale project exploration.

- **Core Components**

- Agent communication mechanism: supports the definition of multiple agents, allowing agents to collaborate with each other to complete tasks through preset or dynamic dialogues; roles, goals, and memory mechanisms can be specified.
- Tool and environment integration: Agent can directly execute code (such as Python snippets), call external APIs, access the file system, etc.; suitable for prototype verification or automated script tasks.
- Task splitting and aggregation: supports splitting large tasks to different agents and then aggregating the results; built-in partial task management logic.
- Dialogue management: supports multi-round dialogue control and context management, can persist or store dialogue history in the short term, and supports backtracking and restarting.

- **Deployment and Operation**

- Self-hosted: The framework is open source and requires you to deploy the Python environment and necessary dependencies yourself; resource consumption depends on the model calling method used (cloud API or local model).
- Operating environment: It can be run locally or on a cloud server. It requires configuration of dependent libraries, containers, or virtual environments. The GPU requirement depends on the specific model call.
- Monitoring logs: You need to integrate the log and monitoring systems yourself to track interactions between agents, tool calls, errors, and performance.

- **SECURITY AND COMPLIANCE**

- Code execution risk: Agent executable scripts need to be run in a controlled environment to prevent malicious or accidental code execution; security can be enhanced through sandbox technology or permission isolation.
- Data access: You need to design your own data access strategy to ensure that sensitive data is only used by authorized agents; encryption and audit mechanisms need to be implemented by yourself.

- **Difficulty of use**

- Suitable for scientific research developers or teams with experimental needs: It can quickly verify multi-agent collaboration ideas, especially in the decomposition and automated execution of complex tasks.
- The learning cost is medium to high: You need to be familiar with the framework API, asynchronous or concurrent management, and tool calling interface; you need to have a deep understanding of code execution security.

- **Typical scenario**

- Automated script generation and execution: such as automated testing, data processing pipelines, and batch task decomposition and execution.
- Multi-agent collaboration research: exploring the performance of different models or strategies in collaborative tasks.
- Internal tools or R&D assistance: such as automated document generation, code review assistants, etc., which require partial automation or complex collaboration.

- **Decision-making recommendations**

- If the R&D team needs to quickly experiment with multi-agent collaboration and have the ability to safely manage code execution, AutoGen can be used.
- If the business scenario does not involve code execution or multi-agent collaboration is weak, consider a lighter framework (such as LangChain + simple Agent).
- The security of the execution environment and the cost of resource usage need to be strictly evaluated.

---

### Flowise detailed function breakdown

- **Positioning and Features**

- A visual drag-and-drop process platform that focuses on process orchestration and multi-tool integration, targeting no-code/low-code users; supports RAG and Agentic RAG, but is not as flexible as a pure code framework.

- **Core Functions**

- Drag nodes: Drag LLM call nodes, retrieval nodes, logic judgment nodes, HTTP request nodes, etc. into the canvas through the graphical interface to form an execution process.
- Real-time debugging: You can view input and output between nodes in real time and quickly adjust prompts or parameters; it is friendly to novices and reduces the threshold for getting started.
- Connectors: Built-in connectors for multiple services (vector database, model API, Webhook, database, message queue, etc.); users can customize connector plug-ins.
- Version management: You can take version snapshots of the process and roll back to the historical state; support team collaboration to edit the process.
- Deployment export: Export the process as a deployable Docker image or Serverless function to facilitate running in a production environment; some platforms may provide one-click deployment to cloud services (requires combination with self-hosting or third-party services).
- Monitoring dashboard: displays process running status, error logs, call counts and time statistics; supports alarm configuration.

- **Deployment and Operation**

- Self-hosted open source: The source code is free and users can deploy it on private servers or clouds. Users need to manage dependencies, container orchestration and monitoring by themselves; suitable for internal platform construction.
- Hosted service (if available): Some services provide hosted versions, which can be quickly experienced and deployed, but privacy and cost must be taken into consideration.
- Scalability: It is very efficient for simple processes; for complex businesses, it may be necessary to embed scripts or custom components in the nodes, increasing maintenance costs.

- **SECURITY AND COMPLIANCE**

- Node security: When connecting to external systems, ensure credential management and network isolation; code nodes must have execution permission control.
- Data privacy: The self-hosted version provides full control over the data; the hosted version requires evaluation of the platform’s encryption and isolation strategies for data storage and transmission.

- **Difficulty of use**

- Low threshold: Non-technical personnel can also quickly build prototypes; technical personnel can expand functions through custom nodes.
- Low learning cost: intuitive interface, less need to write code; suitable for early verification or business teams to independently build lightweight applications.

- **Typical scenario**

- Business team prototype: quickly build knowledge questions and answers, automated processes or simple agents.
- Cross-team collaboration: Product and operations can configure processes without deep coding, and development can then maintain complex nodes.
- Edge scenarios: Export processes to edge devices or lightweight cloud services for distributed small-scale deployment.

- **Functional Requirements Comparison**

- **Deep document understanding**: Ragflow is better than most low-code platforms; but if you only need general RAG, Dify/FastGPT is enough.
- **Multi-agent collaboration**: CrewAI/AutoGen is focused and suitable for complex division of labor scenarios; ordinary processes can use LangChain Agent or the simple Agent function of the low-code platform.
- **Multi-model routing and optimization**: Most platforms support basic routing; if you need refined strategies (dynamic budget control, online learning routing), you need to implement the strategy logic yourself in frameworks such as LangChain.
- **Monitoring and visualization**: SaaS platforms usually have built-in visualization panels; self-hosted frameworks need to integrate their own monitoring systems.
- **Scalability**: All open source solutions are scalable, but require operation and maintenance; SaaS platform expansion is limited by subscription tiers, and the cost increase after growth needs to be evaluated.

---

### 5.4. GPU self-hosted open source model

#### 5.4.1 GPU self-hosting price reference (on demand, converted to RMB ¥)

| Platform     | GPU Model                | Video Memory | On-Demand ¥/h | Spot ¥/h | Notes                                                   |
| ------------ | ------------------------ | ------------ | ------------- | -------- | ------------------------------------------------------- |
| RunPod       | H100 80 GB (PCIe)        | 80G          | 14.43         | —        | Community-based GPU cloud with competitive prices.      |
|              | A100 80 GB (PCIe)        | 80G          | 8.63          | —        |                                                         |
| CoreWeave    | H100 80 GB SXM           | 80G          | 34.44         | —        | Designed for AI, billed by the second.                  |
|              | A100 80 GB               | 80G          | 16.02         | —        |                                                         |
| Lambda Labs  | H100 80 GB SXM           | 80G          | 21.68         | —        | Price reference for 8x GPU configuration.               |
|              | A100 80GB SXM            | 80G          | 12.98         | —        |                                                         |
| Vast.ai      | H100 80 GB               | 80G          | 15.01         | —        | One of the lowest prices on the market.                 |
|              | A100 80 GB               | 80G          | 7.40          | —        |                                                         |
| Hyperstack   | A100 80 GB               | 80G          | 6.89          | —        | Competitively priced.                                   |
| TensorDock   | A100 80 GB (PCIe)        | 80G          | 10.88         | 4.86     | Community GPU cloud with Spot instances.                |
| Azure        | H100 80 GB (PCIe)        | 80G          | 36.25         | 20.23    | Flagship GPU, Spot instances are at risk of preemption. |
|              | A100 80 GB (PCIe)        | 80G          | 18.13         | 7.55     |                                                         |
| Google Cloud | H100 80 GB               | 80G          | 43.50         | —        | Reference for mainstream cloud vendors.                 |
|              | A100 80 GB               | 80G          | 29.00         | —        |                                                         |
| AWS          | H100 80 GB (p5.48xlarge) | 80G          | 28.51         | —        | Price reference for 8x H100 instances.                  |
|              | A100 40 GB (g5.xlarge)   | 24G          | 8.63          | —        | For small to medium models.                             |

#### 5.4.2 Detailed description

- **Cost Model**

- Total Cost of Ownership (TCO): In addition to GPU rental (hourly or with reservation discounts), this also includes server build, power consumption, network bandwidth, storage, software licensing, and operations staff costs.
- Fixed cost and marginal cost: GPU rental is a fixed cost. When the utilization rate is high, the unit token cost is extremely low. If the load is insufficient or idle, the cost efficiency decreases.
- Cost examples: Examples of annual costs of running some models on cloud instances, with unit costs dropping significantly at high utilization.
- Optimize costs: Using quantized models, choosing the right inference framework, and optimizing the inference environment can significantly reduce VRAM requirements and inference costs.

- **Online speed and deployment complexity**

- Highest technical threshold: A professional MLOps team is required to manage hardware, operating systems, drivers, deep learning frameworks, and inference engines.
- Complexity management: involves model deployment, inference optimization, model management, computing power management, load balancing and fault recovery, etc.
- Ongoing maintenance: LLM requires ongoing maintenance, including regular updates and retraining to avoid model drift.
- Open source toolchain: Open source projects can be used to accelerate deployment and optimization.

- **Function Support**

- Fully autonomous: You can deploy any open source model and fine-tune it according to your needs.
- Self-built RAG: deploy vector database, customize index and retrieval strategies, and combine with private knowledge base without relying on external services.
- Agent Workflow: Deeply customize the calling logic, connect to internal systems, enterprise databases, and third-party APIs, and fully control the process.
- Stay flexible: New open source models and optimization tools can be introduced at any time.

- **Free Quota**

- No direct free service from manufacturers; you can apply for cloud vendor computing power coupons or use support to get discounts.
- During the experimental phase, you can use the free inference API to verify functions, or obtain temporary computing power with the help of partners.

- **Compliance**

- Maximum data control: Enterprises have full control over their data, ensuring that data resides in designated regions and enforcing internal privacy and security policies.
- Full responsibility: All responsibilities related to data privacy, security, and compliance are borne by the enterprise, and an internal AI governance framework needs to be established, including data usage policies, access controls, audit logs, and data breach response mechanisms.
- Security risks: Open source frameworks and self-hosted deployments may have insecure default settings and configuration flaws, requiring enhanced security management.

- **Typical scenario**

- Question and answer of internal knowledge base, confidential data reasoning, and legal/medical high compliance scenarios.
- High-concurrency long-term service. When the call volume reaches more than one million times per day, self-hosting has obvious advantages in unit cost; highly customized differentiated products are possible.
- During the product maturity stage, we hope to get rid of external dependence, optimize long-term TCO and enhance technological moat.

- **Challenges and Countermeasures**

- High O&M investment: Establish or train an MLOps team to improve monitoring, scaling, and fault recovery processes; start with small-scale pilots to accumulate experience in stages.
- High technical threshold: Use community best practices, open source tool chains and cloud market images to reduce initial costs; conduct internal training and external consulting.
- Resource management: Improve resource utilization and avoid idle waste through automatic elastic scaling, request caching, and hybrid scheduling (API fallback).

---

## 65. Three-year TCO simulation

**Assumptions:**

- PoC/Beta initial stage (Year 1): 1 million requests per month, 1,000 tokens per request (500 input + 500 output). Total token volume 1 billion tokens/month.
- Initial Scaling (Year 2): 10 million requests per month, 1,000 tokens per request. Total token volume 10 billion tokens per month.
- Scale (Year 3): 30 million requests per month, 1,000 tokens per request. Total token volume 30 billion tokens per month.
- API cost: Average cost calculation based on the sample model.
- GPU Cost: Estimate processing power and cost using sample cloud rental GPU prices.
- Operation and maintenance manpower cost: estimated based on annual cost, with different manpower inputs at different stages.
- Other costs: including storage, network, software licenses, etc., estimated at 10% of the total cost.

| Scheme                               | Year 1 (¥) | Year 2 (¥) | Year 3 (¥) | Total for 3 years (¥) | Remarks                                                                                                                                                                                 |
| ------------------------------------ | ---------- | ---------- | ---------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pure API                             | 130,500    | 1,305,000  | 3,915,000  | 5,350,500             | Cost increases linearly with usage, no upfront investment, and low operation and maintenance costs.                                                                                     |
| Cloud hosting (Azure/AWS)            | 435,000    | 2,175,000  | 4,350,000  | 6,960,000             | Including hosting service fees, model call fees, and some operation and maintenance labor. Year 2/3 Assuming that the unit cost is reduced through reserved instances and optimization. |
| Hybrid strategy (API + self-hosting) | 580,000    | 1,812,500  | 3,262,500  | 5,655,000             | API is the main focus in the PoC/Beta phase, and gradually migrates to self-hosting in the Scale phase. Includes API costs, GPU rental, and operation and maintenance manpower.         |
| Pure self-hosting (H100 cluster)     | 1,087,500  | 2,900,000  | 5,075,000  | 9,062,500             | Including GPU rental, operation and maintenance personnel, electricity, network, etc. Year 1 The investment is large, but the unit cost is the lowest under high utilization.           |

**illustrate:**

- Year 1 (PoC/Beta early stage): Pure API has the lowest cost, mainly using free quotas; cloud hosting requires reserved infrastructure and monitoring; self-hosting requires purchasing/renting GPUs and investing in operation and maintenance, which has the highest cost.
- Year 2 (Beta→ Initial Scale): Pure API costs increased significantly; cloud hosting can control costs through discounts and elastic expansion; self-hosting expands clusters and recruits MLOps personnel, costs increase but unit costs decrease.
- Year 3 (Scale): Pure API costs range from hundreds of thousands to millions; cloud hosting is still expensive at high scale; hybrid strategies show advantages with self-hosting, and the total TCO is more controllable; pure self-hosting has the lowest cost after large-scale, but the initial investment and risk are greater.
- Inflection point analysis: When the monthly call volume exceeds hundreds of millions of tokens, the unit cost of self-custody begins to be lower than that of API, and advance planning is required. The hybrid solution can smoothly transition and switch in stages to alleviate cash flow pressure.
- Sensitivity considerations: If you need the latest large model features or fast iteration capabilities, API has obvious advantages; if you pay more attention to cost and data sovereignty, self-hosting is preferred. A comprehensive assessment based on team capabilities and business needs is required.

---

## 7. Risk and Compliance Assessment

| Risk                | Severity | Mitigation                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vendor lock-in      | High     | Strategy: Introduce an abstract routing layer (API Gateway) in the architecture design. The upper layer calls a unified interface, and the bottom layer can flexibly switch model vendors. And gradually introduce self-hosting as a "ballast stone" to reduce dependence on a single external vendor.                                                                                |
| Data Outbound       | High     | Strategy: If the target user is in mainland China, you must choose a domestic data center or domestic API. It is prohibited to send data containing personal information of Chinese users overseas.                                                                                                                                                                                   |
| Cost out of control | Medium   | Strategy: Establish a refined cost monitoring and budget warning system; set a spending cap for the development/test environment; accurately measure the token consumption of each function point; reduce repeated calls through a layered model and cache common requests; dynamically adjust traffic distribution to avoid bill explosion.                                          |
| Operational Gap     | Medium   | Strategy: Use gradual introduction: Use zero/low operation APIs and hosting solutions in the early stage; recruit or develop MLOps capabilities 3-6 months in advance before deciding to self-host; external consulting and training can be used to accelerate team growth.                                                                                                           |
| Content supervision | Medium   | Strategy: Incomplete trust model with built-in security; add input/output bidirectional content filtering at the business layer and maintain a dynamic sensitive word library; design manual sampling or appeal process for high-risk scenarios (UGC, etc.); improve user agreements and disclaimers; and complete algorithm filing and security audits for domestic public services. |
| Data Privacy        | High     | Policy: Desensitize/anonymize sensitive data; implement role-based access control (RBAC); enable comprehensive audit logs; ensure data residency meets regulatory requirements; prepare for “right to be forgotten” requests.                                                                                                                                                         |
| Model Drift         | Medium   | Strategy: Establish a continuous model performance monitoring mechanism; regularly update and retrain the model to adapt to changes in data and user behavior.                                                                                                                                                                                                                        |

**illustrate:**

- **Vendor lock-in**: Keep the architecture flexible and avoid deep coupling to specific services; plan the self-hosting path in advance.
- **Data outbound transfer**: A compliance red line. You must comply with domestic laws and regulations and use domestic Regions or domestic APIs.
- **Cost out of control**: strict monitoring, budget alerts, and cost optimization through technical strategies (tiered model, caching).
- **Operation gap**: Use low-operation solutions in the early stage to gradually build team capabilities and ensure sufficient support when self-hosting.
- **Content supervision**: Establish a multi-level filtering and manual review mechanism to ensure compliance and security of output.
- **Data Privacy**: Built-in privacy protection mechanisms in the LLM architecture, such as data masking, access control, and auditing.
- **Model drift**: Maintain model performance and relevance through continuous monitoring and regular updates/retraining.

---

## 8. Implementation Roadmap (18 months) (Gantt chart + description)

![Generative AI Deployment Strategy Roadmap 2](./pictures/roadmap2.svg)

**illustrate:**

- **PoC phase (0–2 months)**: Quickly select third-party API + low-code platform, build MVP, conduct preliminary stress and cost testing, and verify core business value.
- **Beta phase (2–8 months)**: Apply for and use cloud vendor startup credits, migrate to cloud-hosted inference endpoints, integrate vector databases to implement RAG, improve monitoring, alerting, and compliance audit processes, conduct A/B testing to introduce self-hosted or small model options, and evaluate quality and cost differences.
- **Scale phase (8–18 months)**: Conduct self-hosted GPU Pilot, verify the performance of open source models and establish MLOps processes; develop intelligent scheduling gateways, migrate regular traffic to self-hosted clusters, and use APIs as alternatives for peak or high-precision needs; continue to optimize performance and costs, improve the team and operation system, and realize a mature and sustainable AI platform.

---

## 9. Conclusion and next steps (key points + explanation)

**ACT NOW**

- Register and obtain an API account such as Alitong Yiqianwen, use Dify Cloud free version or Coze to quickly build a PoC (such as an intelligent FAQ robot or copy generation), and complete the first demonstrable version within 3 weeks.
- Carry out stress tests (such as k6) in parallel to accurately measure the average token consumption and latency of a single request, providing data support for subsequent architectural decisions.

**Short-term planning (Next 2 Weeks)**

- Prepare and submit free quota applications for Azure Founders Hub, AWS Activate, Alibaba Cloud Entrepreneur Program, etc. based on stress test data.
- Started to build a preliminary monitoring and cost tracking system to monitor and alert on API call costs in real time.

**Medium-term goal (Next 3-6 Months)**

- After obtaining cloud vendor credits, migrate to cloud-hosted inference services and deploy them in compliant areas; integrate vector databases to build enterprise-level RAGs to handle medium concurrency and real business scenarios.
- Conduct A/B testing: Use self-hosting or lightweight open source models for some requests to evaluate output quality and cost and accumulate self-hosting experience.
- Improve compliance and security: build input and output two-way filtering, log auditing and manual review processes, and prepare algorithm filing materials.

**Long-term strategy (Next 6-12 Months)**

- Launched the self-hosted GPU Pilot project to conduct small-scale experiments in a cloud computing environment to verify the performance and cost of open source models.
- Establish MLOps processes: automatic expansion and contraction, rolling upgrades, monitoring and alarming, fault recovery, etc., to lay the foundation for large-scale deployment.
- Design and implement an intelligent traffic scheduling gateway to dynamically route between self-hosted clusters and third-party APIs based on request type, cost budget, and system load.

**Final Vision (18 Months)**

- Migrate regular traffic (estimated to be ~70%) to self-hosted clusters to handle it at the lowest unit cost; use third-party APIs as an alternative for peak traffic or as an elastic resource for calling high-performance models.
- Through continuous optimization (model distillation, small model collaboration, caching strategy, long-term reservation discount negotiation, etc.), the long-term TCO is reduced by more than 60% compared to the pure API solution.
- Build a complete compliance and safety operation system: real-time audit, manual sampling, emergency offline mechanism, and regular compliance reporting.
- Team organization: There is no need for full-time MLOps in the PoC phase; a small number of ML/DevOps engineers are introduced in the Beta phase; in the Scale phase, the AI ​​platform team is expanded to form a unified calling platform to provide shared AI services for multiple business scenarios.
- Technology accumulation: Establish documents and best practices, continue to pay attention to open source and industry trends, continuously improve capabilities, and maintain competitive advantage.

---

## 10. References

1. OpenAI. (2025, June 13). API Pricing. Retrieved from [https://openai.com/api/pricing/](https://openai.com/api/pricing/)
2. Baidu. (2025, April 25). Baidu founder Robin Li officially launched the third "Wenxin Cup" Entrepreneurship Competition. Retrieved from [https://www.cls.cn/detail/2015053](https://www.cls.cn/detail/2015053)
3. Tencent Cloud. (2025, May 22). Tencent announced a comprehensive price reduction for Hunyuan large models. Hunyuan-lite is now free. Retrieved from [https://www.stcn.com/article/detail/1212140.html](https://www.stcn.com/article/detail/1212140.html)
4. Anthropic. (2025, June 13). Pricing. Retrieved from [https://www.anthropic.com/pricing](https://www.anthropic.com/pricing)
5. Google AI. (2025, June 13). Gemini API Pricing. Retrieved from [https://ai.google.dev/gemini-api/docs/pricing](https://ai.google.dev/gemini-api/docs/pricing)
6. Baidu. (2025, March 16). Baidu Unveils ERNIE 4.5 and Reasoning Model ERNIE X1. Retrieved from [https://www.prnewswire.com/news-releases/baidu-unveils-ernie-4-5-and-reasoning-model-ernie-x1--makes-ernie-bot-free-ahead-of-schedule-302402490.html](https://www.prnewswire.com/news-releases/baidu-unveils-ernie-4-5-and-reasoning-model-ernie-x1--makes-ernie-bot-free-ahead-of-schedule-302402490.html)
7. Analytics Vidhya. (2025, March). Baidu ERNIE 4.5 & X1: Multimodal AI meets logical thinking. Retrieved from [https://www.analyticsvidhya.com/blog/2025/03/ernie-4-5-x1/](https://www.analyticsvidhya.com/blog/2025/03/ernie-4-5-x1/)
8. DeepSeek. (2025, June 13). Models & Pricing. Retrieved from [https://api-docs.deepseek.com/quick_start/pricing](https://api-docs.deepseek.com/quick_start/pricing)
9. Alibaba Cloud. (2025, June 13). DashScope Models. Retrieved from [https://www.alibabacloud.com/help/en/model-studio/models](https://www.alibabacloud.com/help/en/model-studio/models)
10. Mistral AI. (2025, June 13). Pricing. Retrieved from [https://mistral.ai/pricing](https://mistral.ai/pricing)
11. Together.ai. (2025, June 13). Pricing. Retrieved from [https://www.together.ai/pricing](https://www.together.ai/pricing)
12. AI/ML APIs. (2025, June 12). Qwen3-235B-A22B API Pricing. Retrieved from [https://aimlapi.com/models/qwen-3-235b-a22b-api](https://aimlapi.com/models/qwen-3-235b-a22b-api)
13. Securities Times. (2025, May 22). “You lower the price, I’ll give it away for free”, large model manufacturers are “killing like crazy”. Retrieved from [https://www.stcn.com/article/detail/1212172.html](https://www.stcn.com/article/detail/1212172.html)
14. EmpathyFirst Media. (2025, June). 10 Game-Changing AI Agent Platforms Transforming Business. Retrieved from [https://empathyfirstmedia.com/ai-agent-sdks/](https://empathyfirstmedia.com/ai-agent-sdks/)
15. RunPod. (2025, June 13). GPU Cloud Pricing. Retrieved from [https://www.runpod.io/pricing](https://www.runpod.io/pricing)
16. AWS. (2025, June 13). Amazon Bedrock Security and Privacy. Retrieved from [https://aws.amazon.com/bedrock/security-compliance/](https://aws.amazon.com/bedrock/security-compliance/)
17. Azure China. (2025, June 13). Azure China region service description. Retrieved from [https://azure.microsoft.com/zh-cn/global-infrastructure/regions/](https://azure.microsoft.com/zh-cn/global-infrastructure/regions/)
18. Huawei Cloud. (2025, June 13). PanGu-alpha Pricing. Retrieved from [https://support.huaweicloud.com/price-pangulm/pangulm_02_0001.html](https://support.huaweicloud.com/price-pangulm/pangulm_02_0001.html)
19. AWS Activate. (2025). AWS Activate Startup Credits. Retrieved from [https://aws.amazon.com/activate/](https://aws.amazon.com/activate/)
20. Google for Startups. (2025). Google Cloud Startup Program. Retrieved from [https://cloud.google.com/startup](https://cloud.google.com/startup)
