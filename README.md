# 🚀 README – Comparação AWS Bedrock vs Microsoft Copilot

## 📌 Visão Geral
Este documento apresenta uma análise detalhada de duas soluções de inteligência artificial: **AWS Bedrock** e **Microsoft Copilot**.  
O objetivo é entender **cada uma separadamente**, suas funcionalidades, público-alvo e limitações, e depois realizar uma **comparação clara**.  

---

## 🟧 AWS Bedrock
### O que é
- Serviço da **Amazon Web Services** que oferece acesso a **Foundation Models (FMs)** de diferentes fornecedores (Anthropic Claude, Cohere, Stability AI, Amazon Titan).  
- É uma **plataforma para desenvolvedores** criarem aplicações de IA generativa sem precisar treinar modelos do zero.  

### Funcionalidades
- **Modelos via API**: acesso unificado a diversos FMs.  
- **Fine-tuning**: ajuste de modelos com dados específicos da empresa.  
- **RAG (Retrieval Augmented Generation)**: conectar modelos a bases internas para respostas contextualizadas.  
- **Agentes Bedrock**: criar fluxos de decisão que chamam APIs e sistemas corporativos.  
- **Governança e segurança**: dados ficam sob controle da AWS, com integração nativa em serviços da nuvem.  

### Terraform
- Bedrock **não gera Terraform sozinho**, mas:  
  - Possui suporte oficial no **Terraform AWS Provider**.  
  - É possível provisionar recursos como *Knowledge Bases*, *Inference Profiles* e permissões IAM via Terraform.  
  - Os modelos hospedados no Bedrock podem ser usados para **escrever código Terraform** (ex.: pedir ao Claude para gerar blocos de configuração).  

### Público-Alvo
- **Desenvolvedores, arquitetos de nuvem e equipes de dados** que precisam construir soluções de IA escaláveis.  

---

## 🟦 Microsoft Copilot
### O que é
- Assistente de IA integrado ao **Microsoft 365** (Word, Excel, Outlook, Teams).  
- Também existe o **GitHub Copilot**, voltado para desenvolvedores.  

### Funcionalidades
- **Produtividade corporativa**: gerar textos, resumos, apresentações, análises em Excel.  
- **Integração nativa com Teams**: sumariza reuniões, sugere tarefas, responde perguntas em tempo real.  
- **Integração com GitHub (GitHub Copilot)**:  
  - Sugere código em tempo real dentro do VS Code ou GitHub Codespaces.  
  - Pode gerar **Terraform**, Python, JavaScript, etc.  
  - Auxilia em commits, pull requests e documentação.  

### Público-Alvo
- **Usuários finais e equipes de negócios** (Microsoft Copilot no 365).  
- **Desenvolvedores** (GitHub Copilot).  

---

## 📊 Comparação Direta

| Aspecto | AWS Bedrock | Microsoft Copilot |
|---------|-------------|-------------------|
| **Natureza** | Plataforma de IA generativa na nuvem | Assistente de produtividade (365) + suporte a devs (GitHub Copilot) |
| **Foco** | Construção de aplicações e agentes de IA | Produtividade e colaboração |
| **Modelos de IA** | Diversos fornecedores (Titan, Claude, etc.) | Microsoft + OpenAI |
| **Terraform** | Suporte oficial via AWS Provider; pode gerar código com modelos | GitHub Copilot pode gerar Terraform diretamente |
| **Integração com GitHub** | Via API/middleware | Nativa (GitHub Copilot) |
| **Integração com Teams** | Precisa de bot customizado | Nativa |
| **Customização** | Fine-tuning, RAG, agentes | Limitada (Copilot 365); contextual (GitHub Copilot) |

---

## ⚙️ Exemplo de Código Terraform (Bedrock)

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_bedrockagent_knowledge_base" "example" {
  name        = "infra-knowledge-base"
  description = "Knowledge base para geração de Terraform"
  role_arn    = "arn:aws:iam::123456789012:role/BedrockRole"
}
