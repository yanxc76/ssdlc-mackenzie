[← Voltar ao perfil](https://github.com/yanxc76)

# SSDLC · Laboratório de desenvolvimento seguro

**Java 21 · Spring Boot · Vue 3 · H2 · Segurança de software**

Aplicação de gerenciamento de usuários usada em uma oficina acadêmica para estudar identificação e correção de vulnerabilidades ao longo do ciclo de desenvolvimento.

> **Ambiente de estudo:** este código contém vulnerabilidades intencionais. Execute localmente em um ambiente de laboratório, sem dados reais ou exposição pública.

## Componentes

| Caminho | Papel |
| --- | --- |
| [backend/](backend/) | API Java 21 com Spring Boot e H2 |
| [frontend/](frontend/) | Interface Vue 3 |
| [.gitleaks.toml](.gitleaks.toml) | Configuração de detecção de segredos |
| [.zap/rules.tsv](.zap/rules.tsv) | Regras de apoio ao OWASP ZAP |
| [.github/workflows/security-scan.yml](.github/workflows/security-scan.yml) | Arquivo reservado para o workflow de segurança |

## Estado da automação

O arquivo `security-scan.yml` está vazio nesta revisão. As ferramentas de segurança fazem parte do roteiro da oficina; o repositório ainda não contém uma pipeline implementada nesse arquivo. Não há badge de execução de CI nem promessa de verificações automáticas já ativas.

## Executar localmente

Requisitos: **JDK 21**, Maven, Node.js compatível com Vue CLI 5 e npm.

```bash
git clone https://github.com/yanxc76/ssdlc-mackenzie.git
cd ssdlc-mackenzie/backend
mvn spring-boot:run
```

Em outro terminal, na pasta `frontend`:

```bash
npm ci
npm run serve
```

A oficina utiliza a API em **http://localhost:8080** e o frontend em **http://localhost:3000**. Confira a URL apresentada pelo terminal ao iniciar os serviços.

## Trilhas da oficina

- Identificação de SQL injection, XSS e falhas de validação.
- Revisão de credenciais e tratamento de dados sensíveis.
- Análise de dependências e configurações de segurança.
- Construção de uma pipeline com ferramentas como Gitleaks, CodeQL, OWASP Dependency-Check e ZAP.

**Origem:** Oficina de SSDLC — Universidade Presbiteriana Mackenzie.

<details>
<summary>Material original da disciplina</summary>

O conteúdo abaixo preserva o enunciado e as orientações originais. Para a estrutura atual do repositório, use a apresentação e os comandos acima.

# 🎓 Oficina SSDLC - Secure Software Development Lifecycle

Este projeto foi criado especialmente para ensinar conceitos de segurança no desenvolvimento de software através da prática.

## ⚠️ AVISO IMPORTANTE

**Este projeto contém vulnerabilidades de segurança INTENCIONAIS para fins educacionais.**

🚨 **NÃO USE ESTE CÓDIGO EM PRODUÇÃO!** 🚨

O objetivo é aprender a identificar e corrigir vulnerabilidades através de ferramentas automatizadas e boas práticas de desenvolvimento seguro.

## 📋 Sobre o Projeto

Este é um sistema simples de gerenciamento de usuários com:
- **Backend**: Java 21 com Spring Boot
- **Frontend**: Vue.js 3
- **Pipeline CI/CD**: GitHub Actions com ferramentas de segurança

## 🎯 Objetivos da Oficina

1. Identificar vulnerabilidades de código (SAST)
2. Identificar vulnerabilidades em dependências (SCA)
3. Detectar secrets e credenciais hardcoded
4. Implementar correções de segurança
5. Configurar pipeline de segurança automatizada

## 🛠️ Configuração do Ambiente

### Pré-requisitos

- **Java 21** (JDK)
- **Maven** 3.8+
- **Node.js** 18+
- **Git**
- **IDE** (IntelliJ IDEA, VS Code, Eclipse, etc.)

### Instalação

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd ssdlc-mackenzie
```

2. **Configure o Backend**
```bash
cd backend
mvn clean install
mvn spring-boot:run
```

O backend estará disponível em: `http://localhost:8080`

3. **Configure o Frontend**
```bash
cd frontend
npm install
npm run serve
```

O frontend estará disponível em: `http://localhost:8081`

## 🔍 Executando as Ferramentas de Segurança

### 1. Secret Scanning (Gitleaks)

Detecta credenciais e secrets hardcoded no código.


### 2. Backend - Análise de Dependências (OWASP Dependency Check)

Identifica vulnerabilidades conhecidas em bibliotecas Java.


### 3. Frontend - Análise de Dependências (npm audit)

Verifica vulnerabilidades em pacotes Node.js.

### 4. Backend/Frontend - Análise Estática de Código (CodeQL)

Detecta bugs e vulnerabilidades no código Java.


### 5. DAST - Análise de Dinamica de Código (OWASP Zap)

Verifica vulnerabilidades das aplicações durante sua execução.

### 6. Backend/Frontend - Compliance & License Check

Verifica o compliance das bibliotecas utilizadas no sistema.


## 📊 Pipeline CI/CD

O projeto inclui uma pipeline do GitHub Actions que executa automaticamente:

- ✅ Secret Scanning
- ✅ OWASP Dependency Check (Backend)
- ✅ CodeQL (Backend/Frontend)
- ✅ npm audit (Frontend)
- ✅ OWASP Zap (Backend/Frontend)

A pipeline é executada automaticamente a cada push/PR na branche `main`.

### Visualizar Resultados da Pipeline

1. Acesse a aba "Actions" no GitHub
2. Clique na execução mais recente
3. Verifique cada job e baixe os relatórios gerados

## 🐛 Tipos de Vulnerabilidades no Projeto

Este projeto contém exemplos de:

### Backend (Java)
- 🔴 SQL Injection
- 🔴 Credenciais hardcoded
- 🔴 Logs de dados sensíveis
- 🔴 Exposição de informações sensíveis
- 🔴 Falta de validação de entrada
- 🔴 CORS mal configurado

### Frontend (Vue.js)
- 🔴 Cross-Site Scripting (XSS)
- 🔴 Secrets hardcoded no código
- 🔴 Falta de sanitização de entrada
- 🔴 Exposição de dados sensíveis
- 🔴 Dependências vulneráveis

## 📚 Atividades Práticas

### Atividade 1: Contrução da Pipeline
1. Criar uma pipeline no GitHub Actions com as ferramentas acima
2. Documente quantas vulnerabilidades foram encontradas
3. Classifique por severidade (Crítica, Alta, Média, Baixa)

### Atividade 2: Análise das Vulnerabilidades
1. Para cada vulnerabilidade encontrada:
   - Identifique o arquivo e linha
   - Entenda o risco de segurança
   - Pesquise sobre o tipo de vulnerabilidade

### Atividade 3: Correção (com orientação do instrutor)
1. Corrija as vulnerabilidades seguindo as orientações
2. Execute novamente as ferramentas para validar
3. Commit das correções

## 📖 Recursos de Aprendizado

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE - Common Weakness Enumeration](https://cwe.mitre.org/)
- [OWASP Dependency Check](https://owasp.org/www-project-dependency-check/)
- [Gitleaks Documentation](https://github.com/gitleaks/gitleaks)
- [CodeQL](https://codeql.github.com/docs/)

## 📝 Licença

Este projeto é para fins educacionais apenas. Use por sua conta e risco.

## 🙋 Suporte

Durante a oficina, não hesite em pedir ajuda aos instrutores!

---

**Desenvolvido para a Oficina de SSDLC - Universidade Presbiteriana Mackenzie**


</details>
