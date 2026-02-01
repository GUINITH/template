# 🚀 README – Estudo Comparativo: AWS Bedrock vs Microsoft Copilot Studio

## 📌 Objetivo do Projeto
O objetivo da equipe é desenvolver um **agente de IA** capaz de:
1. **Gerar código Terraform** para provisionar infraestrutura.  
2. **Salvar o código em arquivos** organizados.  
3. **Versionar automaticamente no GitHub** (commit/push).  
4. Executar pipelines já existentes para aplicar o Terraform.  

Este documento compara duas plataformas de IA — **AWS Bedrock** e **Microsoft Copilot Studio** — e descreve caminhos possíveis para atingir esse objetivo.

---

## 🟧 AWS Bedrock
### O que é
- Serviço da **Amazon Web Services** que oferece acesso a **Foundation Models (FMs)** de fornecedores como Anthropic Claude, Cohere, Stability AI e Amazon Titan.  
- Voltado para **desenvolvedores e arquitetos de nuvem** que precisam construir aplicações de IA escaláveis.  

### Como atingir o objetivo
- **Geração de código Terraform**:  
  - Usar modelos hospedados no Bedrock (ex.: Claude) para gerar blocos Terraform sob demanda.  
  - Exemplo: pedir ao modelo para criar configuração de VPC, EKS ou S3.  
- **Salvar em arquivos**:  
  - Middleware (Lambda ou aplicação Python) recebe o código gerado e grava em arquivos `.tf`.  
- **Versionar no GitHub**:  
  - Usar API do GitHub para commit/push automático.  
- **Execução de pipeline**:  
  - Já existente, apenas consome os arquivos versionados.  

### Sugestão de Caminho
1. Criar um **middleware** que conecta Bedrock → GitHub.  
2. Definir prompts padrão para geração de módulos Terraform.  
3. Usar **Terraform AWS Provider** para provisionar recursos Bedrock e manter consistência.  

---

## 🟦 Microsoft Copilot Studio
### O que é
- Plataforma da Microsoft dentro da **Power Platform** para criar e personalizar agentes de IA sem código.  
- Foco em **automação de processos empresariais** e integração com **Teams** e **Microsoft 365**.  

### Como atingir o objetivo
- **Geração de código Terraform**:  
  - Copilot Studio não gera código diretamente como Bedrock, mas pode ser configurado para **chamar APIs externas** (ex.: GitHub Copilot ou serviços customizados).  
  - Pode orquestrar fluxos que acionam serviços de geração de código.  
- **Salvar em arquivos**:  
  - Usar conectores para GitHub ou SharePoint para armazenar os arquivos.  
- **Versionar no GitHub**:  
  - Conector nativo para GitHub pode criar issues, commits ou PRs.  
- **Execução de pipeline**:  
  - Pode acionar pipelines via GitHub Actions ou Power Automate.  

### Sugestão de Caminho
1. Criar um **agente no Copilot Studio** que recebe solicitações de infraestrutura.  
2. Configurar o agente para chamar um serviço externo que gera o Terraform (ex.: GitHub Copilot ou API própria).  
3. Usar conectores do Copilot Studio para salvar e versionar no GitHub.  
4. Integrar diretamente ao Teams para colaboração e acompanhamento.  

---

## 📊 Comparação Direta

| Aspecto | AWS Bedrock | Microsoft Copilot Studio |
|---------|-------------|--------------------------|
| **Natureza** | Plataforma de IA generativa na nuvem | Plataforma low-code/no-code para criar agentes |
| **Foco** | Construção de aplicações e infraestrutura de IA | Automação de processos e colaboração |
| **Geração de Terraform** | Sim, via modelos de IA | Indireto, via conectores ou APIs externas |
| **Salvar em arquivos** | Middleware customizado | Conectores (GitHub, SharePoint) |
| **Versionamento GitHub** | API/middleware | Conector nativo |
| **Integração com Teams** | Precisa de bot customizado | Nativa |
| **Público-alvo** | Desenvolvedores e arquitetos | Usuários corporativos e analistas |

---

## 📌 Conclusão
- **AWS Bedrock**:  
  - Melhor opção se o foco é **gerar código Terraform diretamente** com modelos de IA.  
  - Requer desenvolvimento de middleware para salvar arquivos e versionar no GitHub.  
  - Foco em **infraestrutura e desenvolvimento técnico**.  

- **Microsoft Copilot Studio**:  
  - Melhor opção se o foco é **automação empresarial e integração com Teams**.  
  - Pode orquestrar fluxos que envolvem geração de código, mas depende de serviços externos para criar Terraform.  
  - Foco em **processos corporativos e colaboração**.  

👉 Em resumo:  
- **Bedrock = motor de geração de código Terraform + integração com GitHub.**  
- **Copilot Studio = orquestrador de fluxos empresariais, com integração nativa ao Teams e GitHub.**  

---

## 🚀 Próximos Passos
1. **Com Bedrock**:  
   - Criar middleware para geração e versionamento de Terraform.  
   - Definir prompts e padrões de infraestrutura.  
   - Integrar ao pipeline já existente.  

2. **Com Copilot Studio**:  
   - Criar agente no Studio para orquestrar solicitações.  
   - Configurar conectores para GitHub e Teams.  
   - Integrar com serviço externo para geração de Terraform.  

3. **Decisão estratégica**:  
   - Se o foco é **infraestrutura técnica** → Bedrock.  
   - Se o foco é **automação corporativa e colaboração** → Copilot Studio.  

