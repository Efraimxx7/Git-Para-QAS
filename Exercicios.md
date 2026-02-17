# 🎯 Exercícios Práticos de Git para QA - Guia Completo

[![Nível: Iniciante a Avançado](https://img.shields.io/badge/Nível-Iniciante%20a%20Avançado-blue)]()
[![Tempo Estimado](https://img.shields.io/badge/Tempo-8--12h-orange)]()
[![Hands-On](https://img.shields.io/badge/Tipo-Hands--On-green)]()

Um conjunto completo de exercícios práticos para Analistas de Qualidade aprenderem Git do básico ao avançado através da prática.

---

## 📋 Índice Geral

- [Sobre os Exercícios](#-sobre-os-exercícios)
- [Pré-requisitos](#-pré-requisitos)
- [Como Usar Este Material](#-como-usar-este-material)
- [Estrutura dos Exercícios](#-estrutura-dos-exercícios)
- [NÍVEL 1: BÁSICO](#-nível-1-básico)
  - [Exercício 1.1: Primeiro Repositório](#exercício-11-primeiro-repositório-de-testes)
  - [Exercícios 1.2 a 1.10](#resumo-exercícios-12-a-110)
- [NÍVEL 2: INTERMEDIÁRIO](#-nível-2-intermediário)
  - [Exercício 2.1: Resolvendo Conflitos](#exercício-21-resolvendo-conflitos-de-merge)
  - [Exercícios 2.2 a 2.10](#resumo-exercícios-22-a-210)
- [NÍVEL 3: AVANÇADO](#-nível-3-avançado)
  - [Exercício 3.2: CI/CD com GitHub Actions](#exercício-32-cicd-com-github-actions-para-testes-automatizados)
  - [Exercícios 3.1, 3.3 a 3.10](#resumo-exercícios-31-33-a-310)
- [Template de Solução](#-template-de-solução)
- [FAQ](#-faq)
- [Recursos Adicionais](#-recursos-adicionais)

---

## 🎯 Sobre os Exercícios

Este material contém **30 exercícios práticos** organizados em 3 níveis de dificuldade, especialmente desenhados para QAs que trabalham com automação de testes.

### O que você vai praticar:

✅ Comandos básicos do Git  
✅ Trabalho com branches  
✅ Resolução de conflitos  
✅ Colaboração via GitHub  
✅ GitFlow para QA  
✅ Casos de uso reais de QA  
✅ Automação com Git Hooks  
✅ Integração CI/CD

### Metodologia:

Cada exercício segue a estrutura:
1. **Contexto QA**: Situação real do dia a dia
2. **Objetivo**: O que você precisa fazer
3. **Passo a passo**: Guia para iniciantes
4. **Validação**: Como saber se acertou
5. **Solução**: Resposta completa

---

## 🔧 Pré-requisitos

Antes de começar, você precisa ter:

- [ ] Git instalado ([Download](https://git-scm.com/downloads))
- [ ] Conta no GitHub ([Criar conta](https://github.com/signup))
- [ ] Editor de texto (VS Code, Sublime, Nano, etc)
- [ ] Terminal/Linha de comando básico
- [ ] Vontade de aprender! 🚀

### Verificar instalação:

```bash
git --version
# Deve mostrar: git version 2.x.x
```

---

## 💡 Como Usar Este Material

### Sugestão de Estudo:

```bash
# 1. Crie uma pasta para praticar
mkdir git-pratica
cd git-pratica

# 2. Siga os exercícios em ordem

# 3. Pratique cada comando várias vezes

# 4. Anote suas dúvidas

# 5. Tente criar variações dos exercícios
```

### Tempo Recomendado:

- **Nível 1:** 2-3 horas (pode fazer em 1 dia)
- **Nível 2:** 3-4 horas (distribuir em 2-3 dias)
- **Nível 3:** 3-5 horas (distribuir em uma semana)

**Total:** 8-12 horas ao longo de 1-2 semanas

---

## 📁 Estrutura dos Exercícios

Cada exercício completo contém:

```
📝 Enunciado
🎯 Contexto QA real
📋 Objetivos claros
🔨 Passo a passo detalhado
✅ Validação (como saber que acertou)
🐛 Problemas comuns
💡 Dicas práticas
🎓 Conceitos aprendidos
📖 Solução completa
```

---

# 📘 NÍVEL 1: BÁSICO

**Para quem:** Nunca usou Git ou usou muito pouco  
**Objetivo:** Dominar comandos essenciais  
**Tempo:** 2-3 horas

---

## Exercício 1.1: Primeiro Repositório de Testes

**Tempo Estimado:** 15 minutos  
**Conceitos:** `git init`, `git add`, `git commit`, `git status`

### 🎯 Contexto QA

Você acabou de entrar em um time de QA e vai começar a criar testes automatizados para um novo projeto. O primeiro passo é criar um repositório Git para versionar seus testes desde o início.

Seu líder técnico pediu que você crie um repositório local e faça o primeiro commit com um arquivo de teste básico.

### 📝 Objetivo

Criar um repositório Git do zero e fazer seu primeiro commit com um arquivo de teste simples.

**O que você precisa fazer:**
1. Criar um diretório para seus testes
2. Inicializar um repositório Git
3. Criar um arquivo de teste Python simples
4. Adicionar o arquivo à staging area
5. Fazer seu primeiro commit

### 🔨 Passo a Passo

#### Para Iniciantes (guiado):

**1. Criar o diretório**

```bash
# Crie uma pasta chamada 'automacao-testes'
mkdir automacao-testes

# Entre na pasta
cd automacao-testes
```

**2. Inicializar Git**

```bash
# Este comando cria um repositório Git vazio
git init
```

**O que aconteceu?** Git criou uma pasta oculta `.git` que vai armazenar todo o histórico do projeto.

**3. Ver status atual**

```bash
git status
```

Você verá:
```
On branch main
No commits yet
nothing to commit
```

**4. Criar arquivo de teste**

Crie um arquivo chamado `test_login.py`:

```python
# test_login.py
def test_login_sucesso():
    """Testa login com credenciais válidas"""
    usuario = "qa_teste"
    senha = "senha123"
    assert usuario == "qa_teste"
    assert senha == "senha123"
    print("✓ Teste de login passou!")

def test_login_falha():
    """Testa login com credenciais inválidas"""
    usuario = "usuario_invalido"
    senha = "senha_errada"
    assert usuario != "qa_teste"
    print("✓ Teste de falha de login passou!")
```

**5. Verificar status novamente**

```bash
git status
```

Agora você verá:
```
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test_login.py
```

**6. Adicionar à staging area**

```bash
git add test_login.py
```

**7. Fazer o commit**

```bash
git commit -m "test: adiciona testes iniciais de login"
```

**8. Ver histórico**

```bash
git log
```

Você verá seu primeiro commit! 🎉

#### Para Experientes (resumido):

```bash
mkdir automacao-testes && cd automacao-testes
git init
# Crie test_login.py com testes de login
git add test_login.py
git commit -m "test: adiciona testes iniciais de login"
git log --oneline
```

### ✅ Validação

**Checklist:**
- [ ] Pasta `automacao-testes` foi criada
- [ ] `git status` mostra "On branch main"
- [ ] Arquivo `test_login.py` existe
- [ ] `git log` mostra pelo menos 1 commit
- [ ] Mensagem do commit segue padrão: "test: descrição"
- [ ] `git status` mostra "nothing to commit, working tree clean"

**Comandos de validação:**

```bash
# Verificar que está em repositório Git
ls -la .git

# Ver histórico
git log --oneline

# Ver status
git status
```

### 🐛 Problemas Comuns

**Problema 1: "git: command not found"**
- **Solução:** Instale Git: https://git-scm.com/downloads

**Problema 2: "Author identity unknown"**
- **Solução:**
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

**Problema 3: "Nothing to commit"**
- **Solução:** Você esqueceu de fazer `git add`

### 💡 Dicas

**Boas práticas de mensagens:**
- `test:` - Adiciona ou modifica testes
- `fix:` - Corrige bug em teste
- `docs:` - Documentação

**Comandos úteis:**
```bash
git status          # Use SEMPRE
git log --oneline   # Histórico resumido
git diff            # Ver mudanças antes de commitar
```

**Desfazer se errou:**
```bash
git restore arquivo.py           # Descarta mudanças
git restore --staged arquivo.py  # Remove da staging
git reset --soft HEAD~1          # Desfaz commit
```

### 🎓 Conceitos Aprendidos

| Conceito | Comando | O que faz |
|----------|---------|-----------|
| **Repositório** | `git init` | Cria repositório Git |
| **Status** | `git status` | Mostra estado dos arquivos |
| **Staging Area** | `git add` | Prepara arquivos para commit |
| **Commit** | `git commit -m` | Salva snapshot do código |
| **Histórico** | `git log` | Mostra histórico de commits |

### 📖 Solução Completa

**Comandos executados:**
```bash
mkdir automacao-testes
cd automacao-testes
git init
# (criar test_login.py)
git add test_login.py
git commit -m "test: adiciona testes iniciais de login"
git log
```

**Resultado esperado:**
- ✅ Repositório criado
- ✅ Arquivo commitado
- ✅ Histórico visível

---

## Resumo: Exercícios 1.2 a 1.10

### Exercício 1.2: Histórico de Commits
**Conceitos:** `git log`, `git show`, `git diff`
- Ver histórico detalhado
- Comparar commits
- Entender diferenças entre versões

### Exercício 1.3: Desfazendo Mudanças
**Conceitos:** `git restore`, `git reset`, `git revert`
- Descartar mudanças não commitadas
- Desfazer commits
- Reverter mudanças

### Exercício 1.4: Ignorando Arquivos
**Conceitos:** `.gitignore`
- Criar .gitignore para projetos QA
- Ignorar logs, reports, screenshots
- Padrões de exclusão

### Exercício 1.5: Primeira Branch
**Conceitos:** `git branch`, `git checkout`
- Criar branches
- Trocar entre branches
- Entender HEAD

### Exercício 1.6: Merge Simples
**Conceitos:** `git merge`
- Unir branches
- Fast-forward merge
- Merge commit

### Exercício 1.7: GitHub Básico
**Conceitos:** `git push`, `git pull`, `git clone`
- Conectar com GitHub
- Enviar código
- Baixar atualizações

### Exercício 1.8: Mensagens de Commit
**Conceitos:** Conventional Commits
- Padrões de mensagem
- Prefixos (test, fix, feat)
- Boas práticas

### Exercício 1.9: Status e Diff
**Conceitos:** Visualização de mudanças
- git status detalhado
- git diff avançado
- Staged vs unstaged

### Exercício 1.10: Tags Básicas
**Conceitos:** `git tag`
- Criar tags
- Versões de release
- Listar tags

---

# 📙 NÍVEL 2: INTERMEDIÁRIO

**Para quem:** Já sabe o básico, quer se aprofundar  
**Objetivo:** Trabalhar em equipe e resolver problemas  
**Tempo:** 3-4 horas

---

## Exercício 2.1: Resolvendo Conflitos de Merge

**Tempo Estimado:** 30 minutos  
**Conceitos:** Merge conflicts, resolução de conflitos

### 🎯 Contexto QA

Você e um colega QA estão trabalhando em paralelo no mesmo projeto de testes. Vocês dois modificaram o mesmo arquivo de teste, cada um em sua própria branch. Agora é hora de fazer merge e vocês precisam resolver os conflitos.

**Situação Real:**
- **Branch main:** Testes originais de login
- **Sua branch:** Você adicionou validação de timeout
- **Branch do colega:** Ele adicionou teste de senha forte

Quando você tenta fazer merge, Git encontra um conflito porque ambos editaram as mesmas linhas.

### 📝 Objetivo

Aprender a identificar, entender e resolver conflitos de merge que são comuns quando múltiplos QAs trabalham no mesmo arquivo.

### 🔨 Passo a Passo

#### Preparação: Criar o Cenário

**1. Criar repositório e estrutura inicial**

```bash
mkdir testes-conflito
cd testes-conflito
git init

# Criar arquivo base
cat > test_login.py << 'EOF'
def test_login_basico():
    """Teste básico de login"""
    usuario = "teste_qa"
    senha = "senha123"
    # TODO: adicionar mais validações
    assert usuario == "teste_qa"
    assert senha == "senha123"
EOF

git add test_login.py
git commit -m "test: adiciona teste básico de login"
```

**2. Criar primeira branch e modificar**

```bash
git checkout -b feature/melhoria-testes

# Adicionar validação de timeout
cat > test_login.py << 'EOF'
import time

def test_login_basico():
    """Teste básico de login com timeout"""
    usuario = "teste_qa"
    senha = "senha123"
    
    # Valida timeout de 3 segundos
    start_time = time.time()
    assert usuario == "teste_qa"
    assert senha == "senha123"
    end_time = time.time()
    assert (end_time - start_time) < 3, "Login demorou mais de 3s"
EOF

git add test_login.py
git commit -m "test: adiciona validação de timeout no login"
```

**3. Simular branch do colega**

```bash
git checkout main
git checkout -b feature/novos-cenarios

# Adicionar validação de senha forte
cat > test_login.py << 'EOF'
import re

def test_login_basico():
    """Teste básico de login com senha forte"""
    usuario = "teste_qa"
    senha = "senha123"
    
    # Valida força da senha
    assert usuario == "teste_qa"
    assert len(senha) >= 8, "Senha deve ter no mínimo 8 caracteres"
    assert re.search(r'\d', senha), "Senha deve conter números"
    assert senha == "senha123"
EOF

git add test_login.py
git commit -m "test: adiciona validação de senha forte"
```

**4. Fazer primeiro merge (vai funcionar)**

```bash
git checkout main
git merge feature/melhoria-testes
```

#### Agora vem o Conflito! 🔥

**5. Tentar merge da segunda branch**

```bash
git merge feature/novos-cenarios
```

**BOOM!** 💥 Você verá:

```
Auto-merging test_login.py
CONFLICT (content): Merge conflict in test_login.py
Automatic merge failed; fix conflicts and then commit the result.
```

#### Resolvendo o Conflito

**6. Ver status do conflito**

```bash
git status
```

Saída:
```
Unmerged paths:
        both modified:   test_login.py
```

**7. Abrir arquivo e ver os marcadores**

Você verá algo assim no `test_login.py`:

```python
<<<<<<< HEAD
import time

def test_login_basico():
    """Teste básico de login com timeout"""
    usuario = "teste_qa"
    senha = "senha123"
    
    # Valida timeout de 3 segundos
    start_time = time.time()
    assert usuario == "teste_qa"
    assert senha == "senha123"
    end_time = time.time()
    assert (end_time - start_time) < 3, "Login demorou mais de 3s"
=======
import re

def test_login_basico():
    """Teste básico de login com senha forte"""
    usuario = "teste_qa"
    senha = "senha123"
    
    # Valida força da senha
    assert usuario == "teste_qa"
    assert len(senha) >= 8, "Senha deve ter no mínimo 8 caracteres"
    assert re.search(r'\d', senha), "Senha deve conter números"
    assert senha == "senha123"
>>>>>>> feature/novos-cenarios
```

**Entendendo os marcadores:**
- `<<<<<<< HEAD`: Início da sua versão
- `=======`: Separador
- `>>>>>>> feature/novos-cenarios`: Fim da versão que está vindo

**8. Resolver o conflito**

**Decisão:** Queremos AMBAS as funcionalidades!

Edite o arquivo para ficar assim:

```python
import time
import re

def test_login_basico():
    """Teste básico de login com timeout e senha forte"""
    usuario = "teste_qa"
    senha = "senha123"
    
    # Valida timeout de 3 segundos
    start_time = time.time()
    
    # Validações básicas
    assert usuario == "teste_qa"
    assert senha == "senha123"
    
    # Valida força da senha
    assert len(senha) >= 8, "Senha deve ter no mínimo 8 caracteres"
    assert re.search(r'\d', senha), "Senha deve conter números"
    
    # Verifica tempo de execução
    end_time = time.time()
    assert (end_time - start_time) < 3, "Login demorou mais de 3s"
```

**Importante:** 
- Remove TODOS os marcadores `<<<<<<<`, `=======`, `>>>>>>>`
- Combine o código de forma lógica

**9. Marcar conflito como resolvido**

```bash
git add test_login.py
git status
```

Verá:
```
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)
```

**10. Finalizar o merge**

```bash
git commit -m "merge: combina validações de timeout e senha forte"
```

**11. Ver resultado**

```bash
git log --oneline --graph --all
cat test_login.py
```

### ✅ Validação

**Checklist:**
- [ ] Conflito foi identificado
- [ ] Arquivo foi editado corretamente
- [ ] Ambas as funcionalidades estão presentes
- [ ] Imports estão corretos (`time` e `re`)
- [ ] `git status` mostra "nothing to commit"
- [ ] Arquivo não tem marcadores de conflito

**Comandos de validação:**

```bash
# Verificar que não há conflitos pendentes
git status

# Ver histórico com branches
git log --oneline --graph --all

# Verificar que não há marcadores
cat test_login.py | grep -E '<<<<<|=====|>>>>>'
# Não deve retornar nada
```

### 🐛 Problemas Comuns

**Problema 1: "Esqueci de remover os marcadores!"**

**Solução:**
```bash
# Desfazer último commit
git reset --soft HEAD~1
# Editar arquivo corretamente
# Commitar novamente
git add test_login.py
git commit -m "merge: combina validações"
```

**Problema 2: "Abortar o merge"**

Se quiser cancelar:
```bash
git merge --abort
```

### 💡 Dicas

**Ferramentas visuais:**
```bash
# Usar merge tool
git mergetool

# Configurar VS Code
git config --global merge.tool vscode
```

**Ver diferenças:**
```bash
git diff                              # Ver diferenças
git diff --name-only --diff-filter=U  # Só arquivos em conflito
```

**Estratégias:**
```bash
# Aceitar versão atual
git checkout --ours test_login.py

# Aceitar versão que está vindo
git checkout --theirs test_login.py

# Depois marcar como resolvido
git add test_login.py
```

⚠️ **Cuidado:** Isso descarta uma das versões completamente!

**Prevenir conflitos:**
- Faça `git pull` frequentemente
- Comunique mudanças grandes
- Use branches de vida curta (1-3 dias)
- Divida trabalho em arquivos diferentes

### 🎓 Conceitos Aprendidos

| Conceito | Descrição |
|----------|-----------|
| **Merge Conflict** | Quando Git não sabe qual versão manter |
| **Marcadores** | `<<<<<<<`, `=======`, `>>>>>>>` indicam conflito |
| **Resolução Manual** | Você decide o que manter |
| **Merge Commit** | Commit especial que une duas branches |

**Quando ocorrem conflitos:**
- Duas pessoas editam mesma linha
- Arquivo deletado em uma branch, modificado em outra
- Mesma função modificada diferente

### 📖 Solução Completa

**Fluxo completo:**
```bash
# Setup
mkdir testes-conflito && cd testes-conflito
git init

# Criar arquivo base
echo "codigo base" > test_login.py
git add . && git commit -m "test: base"

# Branch 1
git checkout -b feature/timeout
echo "codigo com timeout" > test_login.py
git add . && git commit -m "test: timeout"

# Branch 2
git checkout main
git checkout -b feature/senha-forte
echo "codigo com senha forte" > test_login.py
git add . && git commit -m "test: senha forte"

# Merge 1 (OK)
git checkout main
git merge feature/timeout

# Merge 2 (CONFLITO!)
git merge feature/senha-forte

# Resolver
# (editar arquivo, remover marcadores)
git add test_login.py
git commit -m "merge: combina funcionalidades"

# Verificar
git log --graph --oneline --all
```

---

## Resumo: Exercícios 2.2 a 2.10

### Exercício 2.2: Stash para QA
**Conceitos:** `git stash`
- Salvar trabalho temporariamente
- Trocar de contexto rápido
- Recuperar mudanças

### Exercício 2.3: Rebase Básico
**Conceitos:** `git rebase`
- Linearizar histórico
- Diferença entre merge e rebase
- Quando usar cada um

### Exercício 2.4: Pull Requests
**Conceitos:** Code review, PR
- Criar PR no GitHub
- Revisar código
- Aprovar mudanças

### Exercício 2.5: Cherry-pick
**Conceitos:** `git cherry-pick`
- Copiar commit específico
- Aplicar em outra branch
- Casos de uso

### Exercício 2.6: Git Blame e Grep
**Conceitos:** Investigação
- Descobrir quem editou
- Buscar no código
- Rastrear mudanças

### Exercício 2.7: Desfazendo Push
**Conceitos:** `git revert`, `git reset`
- Reverter commits públicos
- Reset vs revert
- Segurança em reverter

### Exercício 2.8: Branches Remotas
**Conceitos:** Remote tracking
- Fetch vs pull
- Push de branches
- Tracking branches

### Exercício 2.9: Amend e Reflog
**Conceitos:** Correção de commits
- Modificar último commit
- Recuperar commits perdidos
- Reflog como seguro

### Exercício 2.10: GitFlow Básico
**Conceitos:** Workflow
- Estrutura de branches
- Feature/hotfix/release
- Fluxo completo

---

# 📕 NÍVEL 3: AVANÇADO

**Para quem:** Quer dominar Git para projetos complexos  
**Objetivo:** Automação e casos avançados de QA  
**Tempo:** 3-5 horas

---

## Exercício 3.2: CI/CD com GitHub Actions para Testes Automatizados

**Tempo Estimado:** 60 minutos  
**Conceitos:** GitHub Actions, CI/CD, Workflows, Automação

### 🎯 Contexto QA

Sua equipe de QA está crescendo e os testes estão ficando cada vez mais numerosos. Manualmente rodar todos os testes antes de cada merge está se tornando inviável e propenso a erros.

O time decidiu implementar CI/CD para:
- ✅ Rodar testes automaticamente a cada push
- ✅ Impedir merge de código que quebra testes
- ✅ Gerar relatórios automáticos
- ✅ Notificar a equipe sobre falhas

### 📝 Objetivo

Configurar um pipeline completo de CI/CD usando GitHub Actions que:

1. Executa testes automaticamente
2. Roda testes em múltiplas versões do Python
3. Gera relatório de cobertura
4. Falha se cobertura for menor que 80%
5. Envia relatórios como artifacts

### 🔨 Passo a Passo

#### Parte 1: Preparar Repositório

**1. Criar estrutura do projeto**

```bash
mkdir projeto-ci-cd
cd projeto-ci-cd
git init
mkdir -p tests src

# Criar código fonte
cat > src/calculadora.py << 'EOF'
class Calculadora:
    """Calculadora simples para testes"""
    
    def somar(self, a, b):
        """Soma dois números"""
        return a + b
    
    def subtrair(self, a, b):
        """Subtrai dois números"""
        return a - b
    
    def multiplicar(self, a, b):
        """Multiplica dois números"""
        return a * b
    
    def dividir(self, a, b):
        """Divide dois números"""
        if b == 0:
            raise ValueError("Não é possível dividir por zero")
        return a / b
EOF

# Criar testes
cat > tests/test_calculadora.py << 'EOF'
import pytest
import sys
import os
sys.path.insert(0, os.path.abspath(os.path.join(os.path.dirname(__file__), '..')))

from src.calculadora import Calculadora

@pytest.fixture
def calc():
    return Calculadora()

def test_somar(calc):
    assert calc.somar(2, 3) == 5
    assert calc.somar(0, 0) == 0

def test_subtrair(calc):
    assert calc.subtrair(5, 3) == 2

def test_multiplicar(calc):
    assert calc.multiplicar(2, 3) == 6

def test_dividir(calc):
    assert calc.dividir(6, 2) == 3

def test_dividir_por_zero(calc):
    with pytest.raises(ValueError):
        calc.dividir(5, 0)
EOF

# Criar requirements.txt
cat > requirements.txt << 'EOF'
pytest==7.4.0
pytest-cov==4.1.0
pytest-html==3.2.0
EOF

# Commit inicial
git add .
git commit -m "feat: adiciona calculadora e testes iniciais"
```

**2. Criar repositório no GitHub**

```bash
# Criar repo no GitHub (via interface ou CLI)
# Conectar e fazer push
git remote add origin https://github.com/SEU-USUARIO/projeto-ci-cd.git
git branch -M main
git push -u origin main
```

#### Parte 2: Configurar GitHub Actions

**3. Criar workflow básico**

```bash
mkdir -p .github/workflows

cat > .github/workflows/tests.yml << 'EOF'
name: 🧪 Testes Automatizados

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    name: Testes Python ${{ matrix.python-version }}
    runs-on: ubuntu-latest
    
    strategy:
      matrix:
        python-version: ['3.9', '3.10', '3.11']
    
    steps:
    - name: 📥 Checkout código
      uses: actions/checkout@v3
    
    - name: 🐍 Configurar Python ${{ matrix.python-version }}
      uses: actions/setup-python@v4
      with:
        python-version: ${{ matrix.python-version }}
    
    - name: 📦 Instalar dependências
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
    
    - name: 🧪 Executar testes
      run: |
        pytest tests/ -v --tb=short
    
    - name: 📊 Gerar cobertura
      run: |
        pytest tests/ \
          --cov=src \
          --cov-report=html \
          --cov-report=term \
          --cov-fail-under=80
    
    - name: 📤 Upload relatório
      if: always()
      uses: actions/upload-artifact@v3
      with:
        name: coverage-report-py${{ matrix.python-version }}
        path: htmlcov/
EOF

git add .github/
git commit -m "ci: adiciona workflow de testes automatizados"
git push
```

**4. Ver execução no GitHub**

```
1. Acesse: https://github.com/SEU-USUARIO/projeto-ci-cd/actions
2. Veja o workflow rodando
3. Aguarde finalizar (≈2 minutos)
```

#### Parte 3: Workflow Avançado

**5. Adicionar validações de qualidade**

```bash
cat > .github/workflows/quality-checks.yml << 'EOF'
name: 🔍 Verificações de Qualidade

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  quality:
    name: Qualidade de Código
    runs-on: ubuntu-latest
    
    steps:
    - name: 📥 Checkout
      uses: actions/checkout@v3
    
    - name: 🐍 Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: 📦 Instalar ferramentas
      run: |
        pip install black flake8 pylint mypy
        pip install -r requirements.txt
    
    - name: 🎨 Verificar formatação (Black)
      run: |
        black --check src/ tests/
      continue-on-error: false
    
    - name: 🔍 Linting (Flake8)
      run: |
        flake8 src/ tests/ --max-line-length=100
      continue-on-error: false
EOF

git add .github/workflows/quality-checks.yml
git commit -m "ci: adiciona verificações de qualidade"
git push
```

**6. Workflow de validação de PRs**

```bash
cat > .github/workflows/pr-validation.yml << 'EOF'
name: 🎯 Validação de Pull Request

on:
  pull_request:
    types: [opened, synchronize, reopened]

jobs:
  validate-pr:
    name: Validar PR
    runs-on: ubuntu-latest
    
    steps:
    - name: 📥 Checkout
      uses: actions/checkout@v3
      with:
        fetch-depth: 0
    
    - name: 📝 Validar título do PR
      run: |
        PR_TITLE="${{ github.event.pull_request.title }}"
        if ! echo "$PR_TITLE" | grep -qE "^(feat|fix|test|docs|refactor|chore|ci):"; then
          echo "❌ Título do PR inválido!"
          echo "Use: tipo: descrição"
          exit 1
        fi
        echo "✅ Título válido: $PR_TITLE"
    
    - name: 📏 Verificar tamanho do PR
      run: |
        FILES_CHANGED=$(git diff --name-only origin/${{ github.base_ref }}...HEAD | wc -l)
        echo "📊 Arquivos alterados: $FILES_CHANGED"
        if [ $FILES_CHANGED -gt 20 ]; then
          echo "⚠️ PR muito grande! Considere dividir."
        fi
EOF

git add .github/workflows/pr-validation.yml
git commit -m "ci: adiciona validação de pull requests"
git push
```

#### Parte 4: Testar o CI/CD

**7. Criar Pull Request**

```bash
git checkout -b test/validar-ci-cd

# Adicionar novo método
cat >> src/calculadora.py << 'EOF'

    def potencia(self, base, expoente):
        """Calcula potência"""
        return base ** expoente
EOF

# Adicionar teste
cat >> tests/test_calculadora.py << 'EOF'

def test_potencia(calc):
    assert calc.potencia(2, 3) == 8
    assert calc.potencia(5, 2) == 25
EOF

git add .
git commit -m "feat: adiciona função de potência com testes"
git push -u origin test/validar-ci-cd

# Criar PR via interface do GitHub
```

**8. Observar workflows**

```
1. Acesse o PR no GitHub
2. Veja os checks rodando:
   ✅ Testes Automatizados
   ✅ Verificações de Qualidade
   ✅ Validação de Pull Request
3. Aguarde todos passarem
4. Faça merge quando verde!
```

### ✅ Validação

**Checklist:**
- [ ] Repositório criado no GitHub
- [ ] Pasta `.github/workflows/` existe
- [ ] Workflow `tests.yml` presente
- [ ] Workflow executa automaticamente
- [ ] Testes rodam em múltiplas versões
- [ ] Relatório de cobertura gerado
- [ ] Artifacts salvos
- [ ] PR validation funciona
- [ ] Todos workflows passando (✅ verde)

**Validação local:**

```bash
# Verificar estrutura
ls -la .github/workflows/

# Rodar testes localmente
pytest tests/ -v --cov=src

# Verificar cobertura
pytest tests/ --cov=src --cov-report=term
```

**No GitHub:**
```
✅ Actions tab mostra workflows
✅ PRs mostram checks
✅ Merge bloqueado se testes falharem
```

### 🐛 Problemas Comuns

**Problema 1: Workflow não executa**

**Causas:**
- Arquivo YAML com erro de sintaxe
- Arquivo não está em `.github/workflows/`

**Solução:**
```bash
# Verificar localização
ls -la .github/workflows/

# Forçar re-trigger
git commit --amend --no-edit
git push --force
```

**Problema 2: Testes falham no CI mas passam localmente**

**Causas:**
- Dependências diferentes
- Python version diferente

**Solução:**
```yaml
# Adicionar debug
- name: 🐛 Debug environment
  run: |
    python --version
    pip list
    pwd
```

### 💡 Dicas Avançadas

**Cachear dependências:**
```yaml
- name: 💾 Cache pip
  uses: actions/cache@v3
  with:
    path: ~/.cache/pip
    key: ${{ runner.os }}-pip-${{ hashFiles('**/requirements.txt') }}
```

**Badge de status:**
```markdown
![Tests](https://github.com/USER/repo/workflows/Tests/badge.svg)
```

**Deploy automático:**
```yaml
- name: 🚀 Deploy
  if: github.ref == 'refs/heads/main' && success()
  run: |
    # Comandos de deploy
```

### 🎓 Conceitos Aprendidos

| Conceito | Descrição |
|----------|-----------|
| **CI/CD** | Integração e Deploy Contínuos |
| **Workflow** | Processo automatizado |
| **Job** | Conjunto de steps |
| **Step** | Ação individual |
| **Matrix** | Executar em múltiplas configurações |
| **Artifact** | Arquivo gerado e salvo |

### 📖 Solução Completa

**Estrutura final:**
```
projeto-ci-cd/
├── .github/
│   └── workflows/
│       ├── tests.yml
│       ├── quality-checks.yml
│       └── pr-validation.yml
├── src/
│   └── calculadora.py
├── tests/
│   └── test_calculadora.py
├── requirements.txt
└── README.md
```

**Workflows configurados:**
1. ✅ Testes em Python 3.9, 3.10, 3.11
2. ✅ Verificações de qualidade
3. ✅ Validação de PRs
4. ✅ Cobertura mínima 80%
5. ✅ Artifacts de relatórios

---

## Resumo: Exercícios 3.1, 3.3 a 3.10

### Exercício 3.1: Git Hooks para Testes
**Conceitos:** Hooks, automação
- Pre-commit hooks
- Pre-push hooks
- Rodar testes antes de commit

### Exercício 3.3: GitFlow Completo
**Conceitos:** Workflow avançado
- Feature/Release/Hotfix branches
- Processo completo
- Equipes grandes

### Exercício 3.4: Bisect para Debug
**Conceitos:** `git bisect`
- Encontrar commit problemático
- Bisect automatizado
- Debug eficiente

### Exercício 3.5: Submodules
**Conceitos:** Repositórios aninhados
- Adicionar submodules
- Atualizar submodules
- Casos de uso

### Exercício 3.6: Rebase Interativo
**Conceitos:** Reescrita de histórico
- Squash commits
- Reordenar commits
- Editar mensagens

### Exercício 3.7: Múltiplos Remotes
**Conceitos:** Remotes avançados
- Fork workflow
- Upstream tracking
- Contribuir para open source

### Exercício 3.8: Massa de Dados Versionada
**Conceitos:** Caso real QA
- Versionar dados de teste
- Sincronizar entre ambientes
- Estratégias de branches

### Exercício 3.9: Integração Jira + Git
**Conceitos:** Rastreabilidade
- Commits linkados a issues
- Smart commits
- Workflow integrado

### Exercício 3.10: Projeto Completo QA
**Conceitos:** Projeto final
- Aplicar tudo aprendido
- Projeto real end-to-end
- Apresentação de portfólio

---

# 📚 Template de Solução

Todas as soluções seguem este formato:

## Estrutura de Solução Completa

### 📋 Resumo
- Comandos principais
- Conceitos trabalhados

### 💡 Solução Passo a Passo
- Explicação detalhada de cada comando
- O que acontece em cada etapa
- Saída esperada

### 🔍 Conceitos Explicados
- Teoria por trás dos comandos
- Por que funciona assim
- Analogias úteis

### 🚀 Variações
- Outras formas de resolver
- Casos alternativos
- Customizações

### 💡 Dicas Avançadas
- Truques e atalhos
- Configurações úteis
- Otimizações

### 🎓 Perguntas e Respostas
- Dúvidas comuns
- Esclarecimentos
- Troubleshooting

---

# ❓ FAQ

### Quanto tempo leva para completar?

**Resposta:** 8-12 horas distribuídas em 1-2 semanas:
- Nível 1: 2-3 horas
- Nível 2: 3-4 horas
- Nível 3: 3-5 horas

### Preciso fazer em ordem?

**Resposta:** Sim, especialmente Níveis 1 e 2. Cada exercício constrói sobre o anterior.

### Posso usar ferramentas visuais?

**Resposta:** Os exercícios são para linha de comando, mas você pode usar ferramentas visuais para visualizar.

### E se eu ficar preso?

1. Leia a seção de **Dicas**
2. Tente variações do comando
3. Veja a **Solução**
4. Pergunte em fóruns/comunidades

### Como sei que acertei?

Cada exercício tem:
- ✅ Checklist de validação
- 🤖 Comandos de verificação
- 📋 Solução completa

### Posso fazer em equipe?

**Sim!** Alguns são melhores em grupo (especialmente conflitos e PRs).

Recomendamos:
- Níveis 1-2: Individual
- Nível 3: Pode ser em dupla/trio

---

# 📚 Recursos Adicionais

### Documentação
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com)
- [Git Book (Português)](https://git-scm.com/book/pt-br/v2)

### Tutoriais Interativos
- [Learn Git Branching](https://learngitbranching.js.org)
- [Git Immersion](https://gitimmersion.com)
- [Oh My Git!](https://ohmygit.org) - Jogo

### Ferramentas
- [GitKraken](https://www.gitkraken.com) - Interface visual
- [SourceTree](https://www.sourcetreeapp.com)
- [GitHub Desktop](https://desktop.github.com)

### Comunidades
- [Stack Overflow - Git](https://stackoverflow.com/questions/tagged/git)
- [Reddit - r/git](https://www.reddit.com/r/git)
- Discord - Git Together

---

# 🎉 Conclusão

Parabéns por ter interesse em dominar Git! 

### Próximos Passos:

1. ⭐ Salve este material
2. 📂 Crie sua pasta de prática
3. 🎯 Comece pelo Exercício 1.1
4. 💪 Pratique todos os dias
5. 🎉 Celebre cada conquista!


---

<div align="center">

**Feito com ☕, 💻 e muito ❤️ por QAs para QAs**

**Bons estudos e excelentes commits!** 🚀

</div>
