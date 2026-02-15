```markdown
🚀 Guia Completo de Git para QA - Do Básico ao Avançado

Um guia completo para Analistas de Qualidade que precisam versionar testes, scripts e documentação.


 📖 Índice

- [Sobre este Guia](#-sobre-este-guia)
- [Por que Git é importante para QA?](#-por-que-git-é-importante-para-qa)
- [Instalação](#️-instalação)
- [Primeiros Passos](#-primeiros-passos)
- [Configuração Inicial](#️-configuração-inicial)
- [Trabalhando com Arquivos](#-trabalhando-com-arquivos)
- [Visualizando Histórico](#-visualizando-histórico)
- [Branches (Ramificações)](#-branches-ramificações)
- [Trabalhando com GitHub](#-trabalhando-com-github)
- [Comandos Essenciais para QAs](#-comandos-essenciais-para-qas)
- [Git Hooks para Automação](#-git-hooks-para-automação)
- [Integração com CI/CD](#-integração-com-cicd)
- [GitFlow para Times de QA](#-gitflow-para-times-de-qa)
- [Casos de Uso Específicos para QA](#-casos-de-uso-específicos-para-qa)
- [Fluxo de Trabalho Completo](#-fluxo-de-trabalho-completo)
- [Resolvendo Problemas](#-resolvendo-problemas)
- [Erros Comuns e Soluções](#-erros-comuns-e-soluções)
- [Boas Práticas](#-boas-práticas)
- [Glossário de Termos](#-glossário-de-termos)
- [Templates .gitignore por Framework](#-templates-gitignore-por-framework)
- [Quiz de Autoavaliação](#-quiz-de-autoavaliação)
- [Cheat Sheet](#-cheat-sheet)
- [Recursos Adicionais](#-recursos-adicionais)
- [Contribuindo](#-contribuindo-com-este-guia)
- [Licença](#-licença)



🎯 Sobre este Guia

Este guia foi criado especialmente para Analistas de Qualidade (QA) que precisam aprender Git de forma prática e objetiva.

O que você vai aprender:

✅ Conceitos básicos do Git  
✅ Como versionar testes automatizados  
✅ Trabalhar com branches  
✅ Colaborar com equipe usando GitHub  
✅ Resolver conflitos  
✅ Fluxos de trabalho para QA  
✅ Automação com Git Hooks  
✅ Integração com CI/CD

Pré-requisitos:

- Conhecimento básico de terminal/linha de comando
- Git instalado no seu computador
- Vontade de aprender!



💡 Por que Git é importante para QA?

Como Analista de Qualidade, você vai usar Git para:

 Versionamento de Testes
- Manter histórico de todos os testes criados
- Voltar para versões anteriores quando necessário
- Acompanhar evolução dos casos de teste

Trabalho em Equipe
- Colaborar com outros QAs sem sobrescrever arquivos
- Revisar testes de colegas (Pull Requests)
- Trabalhar em paralelo em diferentes funcionalidades

Organização
- Separar testes por funcionalidade (branches)
- Documentar mudanças com commits descritivos
- Manter código limpo e organizado

Rastreabilidade
- Saber quem criou cada teste
- Entender por que mudanças foram feitas
- Ligar testes a histórias/bugs específicos

Automação
- Integrar com CI/CD
- Executar testes automaticamente
- Gerar relatórios de cobertura

Exemplo Real:
- Sem Git: 10 QAs editando "testes_finais_v2_final_DEFINITIVO.zip"
- Com Git: Cada QA trabalha em sua branch, histórico completo, rollback fácil, zero conflitos



⚙️ Instalação

Linux (Ubuntu/Debian/Mint)


sudo apt update
sudo apt install git
```

### Windows

1. Baixe e instale: https://git-scm.com/download/win
2. Durante a instalação, mantenha as opções padrão

### Mac

```bash
brew install git
```

Ou baixe: https://git-scm.com/download/mac

### Verificar Instalação

```bash
git --version
```

Deve aparecer algo como: `git version 2.40.0`

---

## 🏁 Primeiros Passos

### Conceitos Fundamentais

#### Repositório (Repo)
- Pasta que contém seus arquivos e todo o histórico de versões
- Pode ser local (seu computador) ou remoto (GitHub)

#### Commit
- Um "snapshot" do seu código em um momento específico
- Como tirar uma foto do estado atual dos arquivos

#### Branch
- Uma linha de desenvolvimento paralela
- Permite trabalhar em funcionalidades sem afetar o código principal

#### Staging Area
- Área de preparação antes do commit
- Você escolhe quais mudanças vão no próximo commit

#### Working Directory
- Os arquivos que você está editando agora
- Onde você faz suas alterações

**Fluxo Básico:**
```
Você edita arquivos → git add → Staging Area → git commit → Repositório Local → git push → GitHub
```

---

## 🛠️ Configuração Inicial

### 1. Inicializar Repositório

```bash
mkdir meus-testes
cd meus-testes
git init
```

**O que aconteceu?**  
Git criou uma pasta oculta `.git` que armazena todo o histórico.

### Primeira Configuração (Obrigatória)

Antes de usar o Git, você precisa configurar seu nome e email:

```bash
git config --global user.name "Seu Nome Completo"
git config --global user.email "seuemail@exemplo.com"
```

**Exemplo:**
```bash
git config --global user.name "Maria Silva"
git config --global user.email "maria.silva@empresa.com"
```

**Por que isso é importante?**  
Cada commit que você faz fica marcado com essas informações. É essencial para rastreabilidade em equipes.

### Verificar Configurações

```bash
git config --global user.name
git config --global user.email
```

Ou ver todas as configurações:
```bash
git config --list
```

### Configurações Recomendadas

Ativar cores no terminal:
```bash
git config --global color.ui auto
```

Definir editor padrão:
```bash
git config --global core.editor nano
```

Opções: `nano`, `vim`, `code` (VS Code), `notepad` (Windows)

Configuração importante para evitar problemas:

**Linux/Mac:**
```bash
git config --global core.autocrlf input
```

**Windows:**
```bash
git config --global core.autocrlf true
```

Isso resolve diferenças de quebra de linha entre sistemas operacionais.

### Configuração Local vs Global

**Global** (aplica para todos os repositórios):
```bash
git config --global user.name "Maria"
```

**Local** (só para o repositório atual):
```bash
git config user.name "Maria QA"
```

**Cenário útil:**  
Email pessoal para projetos pessoais, email corporativo para trabalho:

```bash
cd projeto-trabalho/
git config user.email "maria@empresa.com"

cd projeto-pessoal/
git config user.email "maria@gmail.com"
```

---

## 📝 Primeiros Comandos

### 1. Verificar Status

```bash
git status
```

**O que mostra:**
- Arquivos modificados
- Arquivos novos (untracked)
- Arquivos prontos para commit (staged)

**Exemplo de saída:**
```
On branch main
No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test_login.py

nothing added to commit but untracked files present
```

### 2. Criar Arquivo de Teste

```bash
echo "def test_login():" > test_login.py
```

Ou crie manualmente com seu editor favorito.

### 3. Adicionar Arquivo à Staging Area

```bash
git add test_login.py
```

Ou adicionar todos os arquivos modificados:
```bash
git add .
```

Verificar o que está staged:
```bash
git status
```

Agora o arquivo aparece em verde, pronto para commit.

### 4. Fazer Commit

```bash
git commit -m "Adiciona teste de login inicial"
```

**Boas práticas de mensagem:**

✅ **Bom:**
- "Adiciona validação de email no teste de cadastro"
- "Corrige bug no teste de checkout"
- "Atualiza massa de dados para ambiente de homologação"

❌ **Ruim:**
- "atualização"
- "commit"
- "mudanças"

**Commit com mensagem mais longa:**
```bash
git commit -m "Implementa testes do fluxo de compra" -m "Cobre cenários: carrinho vazio, produto indisponível, cupom inválido"
```

### 5. Visualizar Histórico

```bash
git log
```

**Saída:**
```
commit a1b2c3d4e5f6... (HEAD -> main)
Author: Maria Silva <maria@empresa.com>
Date:   Mon Dec 30 10:30:00 2024 -0300

    Adiciona teste de login inicial
```

**Versão resumida:**
```bash
git log --oneline
```

**Saída:**
```
a1b2c3d Adiciona teste de login inicial
```

---

## 🔍 Trabalhando com Arquivos

### Ver Diferenças (DIFF)

Ver mudanças não commitadas:
```bash
git diff
```

**Exemplo de saída:**
```diff
diff --git a/test_login.py b/test_login.py
index a1b2c3d..e5f6g7h 100644
--- a/test_login.py
+++ b/test_login.py
@@ -1,3 +1,4 @@
 def test_login():
-    assert True
+    assert login_page.click_button()
+    assert login_page.verify_success_message()
```

- Linhas com `-` foram removidas (vermelho)
- Linhas com `+` foram adicionadas (verde)

Ver diferenças dos arquivos staged:
```bash
git diff --staged
```

Ver diferenças de arquivo específico:
```bash
git diff test_login.py
```

Comparar com commit anterior:
```bash
git diff HEAD~1
```

### Remover da Staging Area

Arquivo foi adicionado por engano:
```bash
git add config_prod.json
git status
```

Ops! Arquivo de produção não deveria ir no commit.

```bash
git restore --staged config_prod.json
```

Agora o arquivo voltou para "untracked", mas as mudanças permanecem.

### Descartar Mudanças Não Commitadas

⚠️ **CUIDADO!** Isso apaga suas alterações permanentemente.

```bash
git restore test_login.py
```

O arquivo volta para o estado do último commit.

Descartar todas as mudanças:
```bash
git restore .
```

### Renomear ou Mover Arquivos

**Jeito errado:**
```bash
mv test_login.py test_authentication.py
git status
```

Git vai mostrar: 1 arquivo deletado, 1 arquivo novo

**Jeito certo:**
```bash
git mv test_login.py test_authentication.py
git status
```

Git entende que foi um rename, não uma deleção + criação.

### Deletar Arquivos

```bash
git rm test_old.py
git commit -m "Remove teste obsoleto"
```

Se quiser manter o arquivo localmente:
```bash
git rm --cached test_old.py
```

### Ignorar Arquivos (.gitignore)

Crie um arquivo chamado `.gitignore` na raiz do projeto:

```bash
nano .gitignore
```

**Conteúdo do .gitignore para projetos de teste:**

```
# Logs de execução
logs/
reports/
*.log

# Screenshots e evidências
screenshots/
evidence/
*.png
*.jpg

# Arquivos temporários
*.tmp
*.temp
.cache/

# Configurações locais
config_local.json
.env
.env.local

# Relatórios de teste
htmlcov/
coverage/
*.xml
*.html

# Python
__pycache__/
*.pyc
*.pyo
venv/
env/
.pytest_cache/

# Node.js
node_modules/
npm-debug.log
package-lock.json

# Java
target/
*.class
*.jar

# IDE
.vscode/
.idea/
*.swp

# Sistema Operacional
.DS_Store
Thumbs.db
```

⚠️ Não precisa colocar todos, isso é apenas uma demonstração. Ao colocar, aperte CTRL + O e ENTER e depois CTRL + X para sair.

**Commitando o .gitignore:**
```bash
git add .gitignore
git commit -m "Adiciona .gitignore com regras para projetos de teste"
```

**Ignorar arquivo já commitado:**
```bash
git rm --cached arquivo_sensivel.json
echo "arquivo_sensivel.json" >> .gitignore
git add .gitignore
git commit -m "Remove arquivo sensível do repositório"
```

---

## 📊 Visualizando Histórico

### Log Básico

```bash
git log
```

Mostra commits completos com hash, autor, data e mensagem.

### Log Resumido

```bash
git log --oneline
```

**Saída:**
```
f3e8d12 Adiciona teste de carrinho
a7b2c45 Corrige validação de email
1d9f8e3 Implementa teste de login
```

### Log com Gráfico de Branches

```bash
git log --oneline --graph --decorate --all
```

**Saída:**
```
* f3e8d12 (HEAD -> main) Adiciona teste de carrinho
| * b4c5e67 (feature/api-tests) Implementa testes de API
|/
* a7b2c45 Corrige validação de email
* 1d9f8e3 Implementa teste de login
```

### Log de Arquivo Específico

```bash
git log test_login.py
```

Mostra apenas commits que modificaram esse arquivo.

### Log com Diferenças

```bash
git log -p
```

Mostra os commits E as mudanças (diff) de cada um.

### Log Filtrado

Últimos 3 commits:
```bash
git log -3
```

Commits de autor específico:
```bash
git log --author="Maria"
```

Commits por data:
```bash
git log --since="2024-01-01"
git log --until="2024-12-31"
git log --since="2 weeks ago"
```

Commits com palavra na mensagem:
```bash
git log --grep="teste"
```

### Ver Commit Específico

```bash
git show a7b2c45
```

Mostra detalhes completos do commit, incluindo as mudanças.

### Quem Modificou Cada Linha (Blame)

```bash
git blame test_login.py
```

**Saída:**
```
a7b2c45 (Maria Silva 2024-03-15 10:30:00 -0300 1) def test_login():
f3e8d12 (João Costa 2024-03-20 14:45:00 -0300 2)     assert login_page.click()
1d9f8e3 (Maria Silva 2024-03-10 09:15:00 -0300 3)     assert True
```

Útil para descobrir quem escreveu determinada linha de código.

---

## 🌿 Branches (Ramificações)

### O que são Branches?

Branches são linhas de desenvolvimento paralelas. Permitem trabalhar em funcionalidades sem afetar o código principal.

**Analogia:**  
Imagine um livro com vários rascunhos. O rascunho principal é a `main`. Você cria um rascunho novo (`feature/novo-capitulo`) para escrever sem bagunçar o original. Quando fica bom, você copia de volta para o principal (merge).

### Branch Main/Master

A branch principal geralmente se chama `main` (padrão moderno) ou `master` (antigo).

Renomear de master para main:
```bash
git branch -m main
```

### Listar Branches

```bash
git branch
```

**Saída:**
```
* main
  feature/api-tests
  bugfix/login-error
```

O asterisco indica a branch atual.

Listar branches remotas também:
```bash
git branch -a
```

### Criar Nova Branch

```bash
git branch feature/teste-carrinho
```

**Convenções de nome para QA:**
- `feature/nome-funcionalidade`
- `bugfix/nome-bug`
- `hotfix/problema-urgente`
- `test/tipo-teste`
- `docs/documentacao`

**Exemplos:**
```bash
git branch feature/testes-api-pedidos
git branch bugfix/corrige-teste-login
git branch test/automacao-checkout
git branch docs/atualiza-readme
```

### Mudar de Branch

```bash
git checkout feature/teste-carrinho
```

**OU** criar e mudar de uma vez:
```bash
git checkout -b feature/teste-pagamento
```

Isso é equivalente a:
```bash
git branch feature/teste-pagamento
git checkout feature/teste-pagamento
```

### Workflow Completo com Branches

```bash
# 1. Criar branch para nova funcionalidade
git checkout -b test/validacao-cpf

# 2. Fazer alterações
echo "def test_cpf_valido():" > test_cpf.py

# 3. Commitar
git add test_cpf.py
git commit -m "Adiciona validação de CPF"

# 4. Voltar para main
git checkout main

# 5. Trazer mudanças da feature branch (merge)
git merge test/validacao-cpf

# 6. Deletar branch (opcional)
git branch -d test/validacao-cpf
```

### Merge (Unindo Branches)

**Cenário:** Você terminou os testes na branch `feature/teste-carrinho` e quer trazer para `main`.

```bash
# 1. Vai para a branch que VAI RECEBER as mudanças
git checkout main

# 2. Traz as mudanças da outra branch
git merge feature/teste-carrinho
```

Se tudo correr bem:
```
Updating a7b2c45..f3e8d12
Fast-forward
 test_carrinho.py | 25 +++++++++++++++++++++++++
 1 file changed, 25 insertions(+)
 create mode 100644 test_carrinho.py
```

### Fast-Forward vs Merge Commit

**Fast-Forward (padrão):**
- Quando não houve commits na main desde que a branch foi criada
- Git apenas move o ponteiro para frente
- Histórico linear

**Merge Commit:**
- Quando houve commits em ambas as branches
- Git cria um commit especial de merge
- Histórico mostra bifurcação

Forçar merge commit:
```bash
git merge --no-ff feature/teste-carrinho
```

### Deletar Branches

Branch local:
```bash
git branch -d feature/teste-carrinho
```

Se a branch não foi mergeada ainda, Git vai avisar. Para forçar:
```bash
git branch -D feature/teste-carrinho
```

Branch remota:
```bash
git push origin --delete feature/teste-carrinho
```

---

## 🌐 Trabalhando com GitHub

### O que é GitHub?

GitHub é uma plataforma online para hospedar repositórios Git.

**Permite:**
- Backup na nuvem
- Colaboração em equipe
- Code Review (Pull Requests)
- CI/CD integrado
- Issues e Project Management

**Alternativas:** GitLab, Bitbucket, Azure DevOps

### Criar Conta no GitHub

1. Acesse github.com
2. Clique em "Sign up"
3. Preencha email, senha, username
4. Verifique email

### Criar Repositório no GitHub

1. Clique no "+" no canto superior direito
2. "New repository"
3. Nome: `meus-testes-automatizados`
4. Descrição: "Testes automatizados do projeto X"
5. Público ou Privado
6. NÃO marque "Initialize with README" (já temos repo local)
7. "Create repository"

### Conectar Repositório Local com GitHub

Após criar o repo no GitHub, copie a URL:
```
https://github.com/seu-usuario/meus-testes-automatizados.git
```

No terminal:
```bash
git remote add origin https://github.com/seu-usuario/meus-testes-automatizados.git
```

Verificar:
```bash
git remote -v
```

**Saída:**
```
origin  https://github.com/seu-usuario/meus-testes-automatizados.git (fetch)
origin  https://github.com/seu-usuario/meus-testes-automatizados.git (push)
```

### Enviar Código para GitHub (Push)

Primeira vez:
```bash
git push -u origin main
```

O `-u` configura a branch para tracking (não precisa mais nas próximas vezes).

Próximas vezes:
```bash
git push
```

Push de branch específica:
```bash
git push origin feature/teste-carrinho
```

### Baixar Código do GitHub (Pull)

Atualizar branch atual:
```bash
git pull
```

Isso é equivalente a: `git fetch` + `git merge`

Pull de branch específica:
```bash
git pull origin main
```

### Clonar Repositório Existente

Pegar URL no GitHub (botão verde "Code")

```bash
git clone https://github.com/empresa/projeto-testes.git
```

Isso cria uma pasta com o nome do repositório contendo todo o código.

Clonar com nome diferente:
```bash
git clone https://github.com/empresa/projeto-testes.git meu-projeto
```

### Fetch vs Pull

**Fetch (buscar):**
```bash
git fetch origin
```

Baixa as mudanças, mas NÃO aplica no seu código. Você pode revisar antes.

**Pull (puxar):**
```bash
git pull origin main
```

Baixa E aplica as mudanças automaticamente. = fetch + merge

**Workflow seguro:**
```bash
git fetch origin                # Baixa mudanças
git log origin/main             # Revisa o que mudou
git diff main origin/main       # Vê as diferenças
git merge origin/main           # Se estiver OK, faz merge
```

### Autenticação no GitHub

**Token de Acesso Pessoal (recomendado):**

1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate new token
3. Selecione permissões: repo, workflow
4. Copie o token (só aparece uma vez!)

Ao fazer push:
- Username: `seu-usuario`
- Password: `cole-o-token-aqui`

**SSH (alternativa mais segura):**
```bash
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
cat ~/.ssh/id_ed25519.pub
```

Copie a chave pública e adicione em: GitHub → Settings → SSH and GPG keys

Alterar remote para SSH:
```bash
git remote set-url origin git@github.com:seu-usuario/repo.git
```

---

## 🎯 Comandos Essenciais para QAs

### Procurar no Código (Grep)

Procurar palavra em todos os arquivos:
```bash
git grep "assert"
```

Procurar em arquivos específicos:
```bash
git grep "TODO" *.py
```

**Exemplos úteis:**
```bash
git grep "@pytest.mark"      # Encontra marcadores de teste
git grep "def test_"         # Encontra funções de teste
git grep "FIXME"             # Encontra código para corrigir
git grep "config_prod"       # Procura referências a produção
git grep -n "login"          # Mostra número da linha
git grep -c "assert"         # Conta ocorrências
```

### Ver Histórico de Arquivo

```bash
git log --follow test_login.py
```

O `--follow` rastreia o arquivo mesmo se foi renomeado.

### Ver Mudanças em Commit Específico

```bash
git show a7b2c45
```

Ver apenas arquivos modificados:
```bash
git show --name-only a7b2c45
```

### Comparar Branches

```bash
git diff main..feature/teste-carrinho
```

Mostra o que tem na feature que não tem na main.

Ver apenas nomes dos arquivos:
```bash
git diff --name-only main..feature/teste-carrinho
```

### Salvar Trabalho Temporariamente (Stash)

**Cenário real:**  
Você está no meio de uma edição, mas precisa urgentemente trocar de branch para corrigir um bug.

```bash
# Você está editando test_checkout.py
git status
# modified: test_checkout.py

# Salva as mudanças temporariamente
git stash

# Agora pode trocar de branch
git checkout bugfix/teste-urgente

# Faz a correção, commita...

# Volta para onde estava
git checkout main

# Recupera as mudanças
git stash pop
```

**Comandos de stash:**
```bash
git stash                       # Salva mudanças
git stash list                  # Lista todos os stashes
git stash show                  # Mostra o que tem no último stash
git stash apply                 # Aplica sem remover
git stash pop                   # Aplica e remove
git stash drop                  # Remove o último stash
git stash clear                 # Remove todos os stashes
```

Stash com mensagem:
```bash
git stash save "WIP: teste de checkout"
```

Aplicar stash específico:
```bash
git stash list
# stash@{0}: WIP: teste de checkout
# stash@{1}: WIP: validação de email

git stash apply stash@{1}
```

### Desfazer Commits

Desfazer último commit (mantém mudanças):
```bash
git reset --soft HEAD~1
```

As mudanças voltam para staging area.

**Cenário:**
```bash
git commit -m "teste"                                        # Ops, mensagem ruim!
git reset --soft HEAD~1                                      # Desfaz o commit
git commit -m "Implementa validação de email no cadastro"   # Mensagem melhor
```

Desfazer commit (mudanças voltam para working directory):
```bash
git reset HEAD~1
```

Ou:
```bash
git reset --mixed HEAD~1
```

Desfazer commit (APAGA mudanças permanentemente):  
⚠️ **MUITO CUIDADO!**

```bash
git reset --hard HEAD~1
```

Desfazer múltiplos commits:
```bash
git reset --soft HEAD~3        # Desfaz últimos 3 commits
```

Desfazer até commit específico:
```bash
git reset --soft a7b2c45
```

### Reverter Commit (Criar Novo Commit)

Diferente de reset, o revert não apaga o histórico. Cria um novo commit que desfaz as mudanças.

```bash
git revert a7b2c45
```

**Quando usar:**
- **Reset:** Para commits que ainda não foram enviados (push)
- **Revert:** Para commits já no GitHub/compartilhados

### Alterar Último Commit

Esqueceu de adicionar arquivo:
```bash
git add arquivo_esquecido.py
git commit --amend --no-edit
```

Alterar mensagem do último commit:
```bash
git commit --amend -m "Nova mensagem melhor"
```

⚠️ Só faça isso em commits que ainda NÃO foram enviados (push)!

### Cherry-pick (Pegar Commit Específico)

**Cenário:**  
Você fez um commit na branch errada e quer copiar para a branch certa.

```bash
# Você está em feature/teste-api
git log --oneline
# f3e8d12 Corrige validação importante

# Vai para a branch correta
git checkout main

# Pega aquele commit
git cherry-pick f3e8d12
```

### Tags (Versões)

Tags são marcadores de versões específicas.

Criar tag:
```bash
git tag v1.0.0
```

Tag com mensagem (anotada):
```bash
git tag -a v1.0.0 -m "Versão 1.0 - Primeira release estável"
```

Enviar tags para GitHub:
```bash
git push origin v1.0.0
```

Enviar todas as tags:
```bash
git push origin --tags
```

Listar tags:
```bash
git tag
```

Ver detalhes de uma tag:
```bash
git show v1.0.0
```

Deletar tag:
```bash
git tag -d v1.0.0

push origin --delete v1.0.0                 # Remota
```

**Tags úteis para QA:**
```bash
git tag -a sprint-23 -m "Testes da Sprint 23"
git tag -a release-2.5.0 -m "Cobertura de testes da release 2.5"
git tag -a stable-tests -m "Versão estável dos testes"
```

---

## 🪝 Git Hooks para Automação (Caso for iniciante em git,não e preciso aprender isso agora,foque no essencial!)

### O que são Git Hooks?

Git Hooks são scripts que executam automaticamente em eventos Git específicos. Perfeitos para automação de testes!

**Localização dos Hooks:**
```
.git/hooks/
```

**Hooks Úteis para QA:**
- `pre-commit`: Executa antes de cada commit
- `pre-push`: Executa antes de cada push
- `post-merge`: Executa após merge
- `post-checkout`: Executa após trocar de branch

### Pre-commit Hook: Executar Testes Antes de Commit

Crie o arquivo `.git/hooks/pre-commit`:

```bash
#!/bin/bash
echo "🧪 Executando testes antes do commit..."

# Executa testes
pytest tests/

# Se falhar, cancela o commit
if [ $? -ne 0 ]; then
    echo "❌ Testes falharam! Commit cancelado."
    exit 1
fi

echo "✅ Todos os testes passaram!"
exit 0
```

Torne executável:
```bash
chmod +x .git/hooks/pre-commit
```

Agora, toda vez que você tentar fazer commit, os testes rodam automaticamente!

### Pre-commit Hook: Validar Formatação de Código

```bash
#!/bin/bash
echo "🔍 Validando formatação do código..."

# Python - Black
black --check tests/
if [ $? -ne 0 ]; then
    echo "❌ Código não está formatado. Execute: black tests/"
    exit 1
fi

# Python - Flake8
flake8 tests/
if [ $? -ne 0 ]; then
    echo "❌ Problemas de linting encontrados!"
    exit 1
fi

echo "✅ Formatação OK!"
exit 0
```

### Pre-push Hook: Validar Antes de Enviar

Crie `.git/hooks/pre-push`:

```bash
#!/bin/bash
echo "🔍 Validando código antes do push..."

# Executa todos os testes
pytest tests/ --verbose

if [ $? -ne 0 ]; then
    echo "⚠️ Alguns testes falharam!"
    read -p "Deseja continuar com o push mesmo assim? (y/n) " -n 1 -r
    echo
    if [[ ! $REPLY =~ ^[Yy]$ ]]; then
        echo "❌ Push cancelado."
        exit 1
    fi
fi

# Verifica cobertura de testes
pytest --cov=. --cov-report=term-missing --cov-fail-under=80

if [ $? -ne 0 ]; then
    echo "⚠️ Cobertura de testes abaixo de 80%!"
    read -p "Continuar mesmo assim? (y/n) " -n 1 -r
    echo
    if [[ ! $REPLY =~ ^[Yy]$ ]]; then
        exit 1
    fi
fi

echo "✅ Validação concluída. Fazendo push..."
exit 0
```

Torne executável:
```bash
chmod +x .git/hooks/pre-push
```

### Post-merge Hook: Atualizar Dependências Automaticamente

Crie `.git/hooks/post-merge`:

```bash
#!/bin/bash
echo "📦 Verificando dependências após merge..."

# Verifica se requirements.txt mudou
if git diff-tree -r --name-only --no-commit-id ORIG_HEAD HEAD | grep --quiet requirements.txt; then
    echo "✨ requirements.txt foi atualizado!"
    echo "📥 Instalando novas dependências..."
    pip install -r requirements.txt
fi

# Verifica se package.json mudou (Node.js)
if git diff-tree -r --name-only --no-commit-id ORIG_HEAD HEAD | grep --quiet package.json; then
    echo "✨ package.json foi atualizado!"
    echo "📥 Instalando dependências..."
    npm install
fi

echo "✅ Verificação concluída!"
```

Torne executável:
```bash
chmod +x .git/hooks/post-merge
```

### Commit-msg Hook: Validar Mensagens de Commit

Crie `.git/hooks/commit-msg`:

```bash
#!/bin/bash

# Lê a mensagem do commit
commit_msg=$(cat "$1")

# Padrão: tipo: descrição
# Ex: test: adiciona validação de CPF
if ! echo "$commit_msg" | grep -qE "^(feat|fix|test|docs|refactor|chore|style): .{10,}"; then
    echo "❌ Mensagem de commit inválida!"
    echo ""
    echo "Use o formato: tipo: descrição"
    echo ""
    echo "Tipos válidos:"
    echo "  feat:     Nova funcionalidade"
    echo "  fix:      Correção de bug"
    echo "  test:     Adiciona/modifica testes"
    echo "  docs:     Documentação"
    echo "  refactor: Refatoração"
    echo "  chore:    Manutenção"
    echo "  style:    Formatação"
    echo ""
    echo "Exemplo: test: adiciona validação de email no cadastro"
    exit 1
fi

echo "✅ Mensagem válida!"
exit 0
```

Torne executável:
```bash
chmod +x .git/hooks/commit-msg
```

### Compartilhar Hooks com a Equipe

**Problema:** Hooks ficam em `.git/hooks/` que não é versionado.

**Solução:** Criar pasta `hooks/` no repositório:

```bash
mkdir hooks
mv .git/hooks/pre-commit hooks/
mv .git/hooks/pre-push hooks/
mv .git/hooks/commit-msg hooks/
```

Criar script de instalação `hooks/install.sh`:

```bash
#!/bin/bash
echo "📥 Instalando Git Hooks..."

cp hooks/pre-commit .git/hooks/
cp hooks/pre-push .git/hooks/
cp hooks/commit-msg .git/hooks/

chmod +x .git/hooks/pre-commit
chmod +x .git/hooks/pre-push
chmod +x .git/hooks/commit-msg

echo "✅ Hooks instalados com sucesso!"
```

Documentar no README:

```markdown
Após clonar o repositório, execute:


bash hooks/install.sh
```
```

 🔄 Integração com CI/CD

O que é CI/CD?

- CI (Continuous Integration): Integração contínua do código
- CD (Continuous Deployment): Deploy contínuo para produção

Para QA: Testes executam automaticamente a cada push/PR!

 GitHub Actions para Testes Automatizados

Crie `.github/workflows/tests.yml`:


name: Testes Automatizados

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout código
      uses: actions/checkout@v3
    
    - name: Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: Instalar dependências
      run: |
        pip install -r requirements.txt
    
    - name: Executar testes
      run: |
        pytest tests/ --html=report.html --self-contained-html
    
    - name: Upload relatório
      uses: actions/upload-artifact@v3
      if: always()
      with:
        name: test-report
        path: report.html
    
    - name: Verificar cobertura
      run: |
        pytest --cov=. --cov-report=xml --cov-report=term
    
    - name: Upload cobertura para Codecov
      uses: codecov/codecov-action@v3
      with:
        file: ./coverage.xml
```

Benefícios:
- ✅ Testes executam em cada push
- ✅ Impede merge de código quebrado
- ✅ Relatórios automáticos
- ✅ Notificações de falhas

 Workflow Avançado: Múltiplos Ambientes

```yaml
name: Testes Multi-Ambiente

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
        python-version: ['3.9', '3.10', '3.11']
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Python ${{ matrix.python-version }}
      uses: actions/setup-python@v4
      with:
        python-version: ${{ matrix.python-version }}
    
    - name: Instalar dependências
      run: |
        pip install -r requirements.txt
    
    - name: Executar testes
      run: |
        pytest tests/ -v
    
    - name: Notificar Slack em caso de falha
      if: failure()
      uses: slackapi/slack-github-action@v1
      with:
        payload: |
          {
            "text": "❌ Testes falharam no ${{ matrix.os }} com Python ${{ matrix.python-version }}"
          }
      env:
        SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}
```

### Workflow: Testes Selenium/Playwright

```yaml
name: Testes E2E

on:
  schedule:
    - cron: '0 2 * * *'  # Executa todo dia às 2h
  workflow_dispatch:  # Permite execução manual

jobs:
  e2e-tests:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: Setup Chrome
      uses: browser-actions/setup-chrome@latest
    
    - name: Instalar dependências
      run: |
        pip install selenium pytest pytest-html
        pip install webdriver-manager
    
    - name: Executar testes E2E
      run: |
        pytest tests/e2e/ --html=report.html --self-contained-html
      env:
        BASE_URL: ${{ secrets.BASE_URL }}
        USERNAME: ${{ secrets.TEST_USERNAME }}
        PASSWORD: ${{ secrets.TEST_PASSWORD }}
    
    - name: Upload screenshots em caso de falha
      if: failure()
      uses: actions/upload-artifact@v3
      with:
        name: screenshots-falha
        path: screenshots/
    
    - name: Upload relatório
      uses: actions/upload-artifact@v3
      if: always()
      with:
        name: e2e-report
        path: report.html
```

### Workflow: Validação de Pull Request

```yaml
name: PR Validation

on:
  pull_request:
    branches: [ main, develop ]

jobs:
  validate:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
      with:
        fetch-depth: 0  # Pega histórico completo
    
    - name: Verificar título do PR
      run: |
        PR_TITLE="${{ github.event.pull_request.title }}"
        if ! echo "$PR_TITLE" | grep -qE "^(feat|fix|test|docs|refactor|chore):"; then
          echo "❌ Título do PR deve seguir o padrão: tipo: descrição"
          exit 1
        fi
    
    - name: Verificar arquivos modificados
      run: |
        FILES_CHANGED=$(git diff --name-only origin/main...HEAD)
        echo "Arquivos modificados:"
        echo "$FILES_CHANGED"
    
    - name: Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: Instalar dependências
      run: pip install -r requirements.txt
    
    - name: Executar apenas testes afetados
      run: |
        pytest tests/ -v --tb=short
    
    - name: Verificar cobertura de novos arquivos
      run: |
        pytest --cov=. --cov-report=term-missing
    
    - name: Comentar no PR
      uses: actions/github-script@v6
      if: always()
      with:
        script: |
          github.rest.issues.createComment({
            issue_number: context.issue.number,
            owner: context.repo.owner,
            repo: context.repo.repo,
            body: '✅ Validação concluída! Testes executados com sucesso.'
          })
```

### Configurar Secrets no GitHub

1. GitHub → Settings → Secrets and variables → Actions
2. New repository secret

**Secrets úteis para QA:**
- `BASE_URL`: URL do ambiente de testes
- `TEST_USERNAME`: Usuário de teste
- `TEST_PASSWORD`: Senha de teste
- `SLACK_WEBHOOK`: Webhook para notificações
- `API_TOKEN`: Token de API de teste

---

## 🌊 GitFlow para Times de QA

### O que é GitFlow?

Um modelo de branching que organiza o desenvolvimento em branches com propósitos específicos.

### Estrutura de Branches GitFlow

```
main (produção)
  ├── develop (desenvolvimento)
  │   ├── feature/nova-funcionalidade
  │   ├── test/automacao-checkout
  │   └── test/validacao-api
  ├── release/v2.0 (preparação release)
  └── hotfix/bug-critico (correção urgente)
```

### Tipos de Branches:

**main/master**
- Código em produção
- Sempre estável
- Só recebe merges de release ou hotfix

**develop**
- Branch de desenvolvimento
- Base para features
- Integração contínua

**feature/**
- Novas funcionalidades ou testes
- Criada a partir de develop
- Merge de volta para develop

**release/**
- Preparação para produção
- Criada a partir de develop
- Merge para main e develop

**hotfix/**
- Correções urgentes em produção
- Criada a partir de main
- Merge para main e develop

### Workflow GitFlow Completo

**1. Desenvolvimento de Novos Testes**

```bash
# Atualiza develop
git checkout develop
git pull origin develop

# Cria feature branch
git checkout -b test/validacao-carrinho

# Desenvolve os testes
# (Cria arquivos test_carrinho.py)

# Commits
git add test_carrinho.py
git commit -m "test: adiciona validação de carrinho vazio"
git commit -m "test: adiciona validação de produtos indisponíveis"

# Push da feature
git push -u origin test/validacao-carrinho

# Abre Pull Request no GitHub
# base: develop ← compare: test/validacao-carrinho

# Após aprovação, merge para develop
git checkout develop
git merge test/validacao-carrinho
git push origin develop

# Deleta a feature branch
git branch -d test/validacao-carrinho
git push origin --delete test/validacao-carrinho
```

**2. Preparação de Release**

```bash
# Cria release branch
git checkout develop
git pull origin develop
git checkout -b release/v2.0

# Últimos ajustes
# Atualiza versão no package.json ou __version__
# Executa todos os testes
# Corrige bugs encontrados

git add .
git commit -m "chore: prepara release 2.0"

# Merge para main
git checkout main
git merge release/v2.0
git tag -a v2.0 -m "Release 2.0 - Novos testes de carrinho e checkout"
git push origin main --tags

# Merge de volta para develop
git checkout develop
git merge release/v2.0
git push origin develop

# Deleta release branch
git branch -d release/v2.0
git push origin --delete release/v2.0
```

**3. Hotfix Urgente em Produção**

```bash
# Bug crítico encontrado em produção!

# Cria hotfix a partir de main
git checkout main
git pull origin main
git checkout -b hotfix/corrige-teste-login

# Corrige o problema
git add test_login.py
git commit -m "fix: corrige timeout no teste de login"

# Merge para main
git checkout main
git merge hotfix/corrige-teste-login
git tag -a v2.0.1 -m "Hotfix: corrige timeout"
git push origin main --tags

# Merge para develop
git checkout develop
git merge hotfix/corrige-teste-login
git push origin develop

# Deleta hotfix branch
git branch -d hotfix/corrige-teste-login
git push origin --delete hotfix/corrige-teste-login
```

### GitFlow Simplificado (para times pequenos)

Se GitFlow completo for complexo demais:

```
main
  ├── develop
  │   ├── feature/teste-1
  │   └── feature/teste-2
  └── hotfix/bug-urgente
```

**Regras simples:**
- Sempre trabalhe em branches separadas
- Features partem de develop
- Hotfixes partem de main
- Use Pull Requests para tudo

### Instalando Git Flow Extension

**Linux:**
```bash
sudo apt install git-flow
```

**Mac:**
```bash
brew install git-flow
```

**Windows:**  
Baixe em: https://github.com/petervanderdoes/gitflow-avh

### Usando Git Flow Extension:

```bash
# Inicializar Git Flow no repositório
git flow init
# Aceite os nomes padrão das branches

# Criar feature
git flow feature start validacao-cpf
# Trabalha normalmente...

# Finalizar feature
git flow feature finish validacao-cpf
# Automaticamente faz merge em develop e deleta a branch

# Criar release
git flow release start 2.0
# Prepara a release...

# Finalizar release
git flow release finish 2.0
# Merge em main e develop, cria tag, deleta branch

# Criar hotfix
git flow hotfix start corrige-login
# Corrige o bug...

# Finalizar hotfix
git flow hotfix finish corrige-login
# Merge em main e develop, cria tag
```

### Estratégia de Branches Alternativa: GitHub Flow

Mais simples que GitFlow. Ideal para deploys frequentes.

```
main
  ├── feature/teste-api
  ├── feature/teste-ui
  └── bugfix/corrige-validacao
```

**Regras:**
- `main` sempre deployável
- Crie branch para qualquer mudança
- Abra PR quando terminar
- Após aprovação, merge para main
- Deploy imediatamente após merge

**Exemplo GitHub Flow:**

```bash
# Cria branch
git checkout -b test/api-pedidos

# Trabalha e commita
git add .
git commit -m "test: adiciona testes de API de pedidos"
git push -u origin test/api-pedidos

# Abre Pull Request

# Após aprovação, merge e deploy
git checkout main
git merge test/api-pedidos
git push origin main
# CI/CD faz deploy automático

# Deleta branch
git branch -d test/api-pedidos
```

### Qual estratégia usar?

- **GitFlow:** Projetos com releases planejadas, múltiplos ambientes
- **GitHub Flow:** Deploys contínuos, times ágeis, produtos web
- **Trunk-Based:** Times muito experientes, deploys múltiplos por dia

**Dicas para Escolher:**
- Time pequeno (1-3 QAs): GitHub Flow
- Time médio (4-10 QAs): GitFlow simplificado
- Time grande (10+ QAs): GitFlow completo

---

## 🎯 Casos de Uso Específicos para QA

### Encontrar Quando um Teste Começou a Falhar

**Problema:** Um teste que funcionava começou a falhar. Qual commit quebrou?

**Solução: Git Bisect**

```bash
git bisect start
git bisect bad                    # Commit atual está quebrado
git bisect good a7b2c45          # Último commit que funcionava

# Git vai testando commits intermediários
# Para cada um, você roda o teste:
pytest test_login.py

# Se passou:
git bisect good

# Se falhou:
git bisect bad

# Git continua dividindo até encontrar o commit exato

# Ao final, Git mostra:
# f3e8d12 is the first bad commit

# Resetar bisect:
git bisect reset
```

**Bisect Automatizado:**

Crie script `test_script.sh`:

```bash
#!/bin/bash
pytest test_login.py
exit $?
```

Automatize o bisect:
```bash
git bisect start
git bisect bad
git bisect good a7b2c45
git bisect run ./test_script.sh
```

Git testa automaticamente e encontra o commit problemático!

### Comparar Cobertura de Testes Entre Branches

```bash
# Gerar relatório na main
git checkout main
pytest --cov=. --cov-report=html
cp -r htmlcov htmlcov_main

# Gerar na feature
git checkout feature/nova-funcionalidade
pytest --cov=. --cov-report=html
cp -r htmlcov htmlcov_feature

# Comparar:
diff htmlcov_main/index.html htmlcov_feature/index.html

# Ou use ferramenta:
coverage-diff htmlcov_main htmlcov_feature
```

### Rastrear Mudanças em Massa de Dados de Teste

```bash
# Ver histórico completo de arquivo:
git log --follow -- data/test_users.json

# Ver quem mexeu em cada linha:
git blame data/test_users.json

# Ver mudanças em commit específico:
git show a7b2c45:data/test_users.json

# Comparar versões:
git diff HEAD~5:data/test_users.json HEAD:data/test_users.json

# Recuperar versão antiga:
git checkout a7b2c45 -- data/test_users.json
```

### Sincronizar Massa de Dados Entre Ambientes

**Problema:** Dados de teste no ambiente dev diferentes do homolog.

**Solução:** Branches por ambiente

```
main (produção)
├── homolog (homologação)
└── dev (desenvolvimento)
```

```bash
# Atualizar dev com dados de homolog:
git checkout dev
git checkout homolog -- data/test_users.json
git commit -m "data: sincroniza usuários com homolog"

# Atualizar homolog com dados de dev:
git checkout homolog
git checkout dev -- data/test_users.json
git commit -m "data: atualiza com novos usuários de dev"
```

### Reverter Teste Específico Sem Afetar Outros

**Cenário:** Você tem 10 commits, mas quer reverter apenas as mudanças do `test_checkout.py`.

```bash
git log --oneline test_checkout.py
# f3e8d12 Adiciona teste de cupom
# a7b2c45 Adiciona teste de frete
# 1d9f8e3 Cria teste inicial

# Reverter commit específico:
git revert a7b2c45

# Ou reverter apenas arquivo:
git checkout a7b2c45~1 -- test_checkout.py
git commit -m "Reverte mudanças no teste de frete"
```

### Trabalhar com Múltiplos Repositórios

**Cenário:** Testes em um repo, aplicação em outro.

```bash
# Adicionar segundo repositório:
git remote add app https://github.com/empresa/aplicacao.git

# Ver todos os remotes:
git remote -v

# Buscar mudanças do app:
git fetch app

# Ver branches do app:
git branch -r

# Checkout de branch do app:
git checkout -b app-feature app/feature/nova-funcionalidade
```

**Git Submodules para Bibliotecas de Teste Compartilhadas:**

```bash
# Adicionar biblioteca compartilhada:
git submodule add https://github.com/empresa/test-utils.git libs/test-utils

# Clonar repo com submodules:
git clone --recursive https://github.com/empresa/meus-testes.git

# Atualizar submodules:
git submodule update --remote
```

### Buscar Testes por Palavra-chave

```bash
# Encontrar todos os testes que usam determinada fixture:
git grep "@pytest.fixture" tests/

# Encontrar testes que testam login:
git grep "def test_.*login" tests/

# Encontrar TODOs em testes:
git grep "TODO" tests/

# Contar quantos testes existem:
git grep -c "def test_" tests/ | awk -F: '{sum+=$2} END {print sum}'

# Encontrar testes que usam determinado locator:
git grep "id=\"login-button\"" tests/
```

### Gerar Relatório de Contribuições da Equipe QA

```bash
# Commits por autor no último mês:
git shortlog -sn --since="1 month ago"

# Linhas adicionadas por autor:
git log --shortstat --since="1 month ago" --author="Maria" | grep "files changed" | awk '{files+=$1; inserted+=$4; deleted+=$6} END {print "Files:", files, "Inserted:", inserted, "Deleted:", deleted}'

# Arquivos mais modificados:
git log --pretty=format: --name-only --since="3 months ago" | sort | uniq -c | sort -rg | head -10

# Atividade por dia da semana:
git log --date=format:'%A' --pretty=format:'%ad' | sort | uniq -c
```

### Arquivar Testes Antigos

**Problema:** Testes antigos que não são mais usados, mas quer manter histórico.

```bash
# Criar branch de arquivo:
git checkout -b archive/testes-antigos-2024

# Mover testes antigos:
git mv tests/old_*.py archived/
git commit -m "archive: move testes antigos para arquivo"
git push origin archive/testes-antigos-2024

# Na main, deletar os arquivos:
git checkout main
git rm tests/old_*.py
git commit -m "remove: testes antigos (arquivados em branch archive/testes-antigos-2024)"

# Recuperar se necessário:
git checkout archive/testes-antigos-2024 -- tests/old_test.py
```

---
```markdown


🔄 Fluxo de Trabalho Completo

 Cenário 1: Criando Novos Testes


# 1. Atualiza repositório
git pull origin main

# 2. Cria branch para seu trabalho
git checkout -b test/validacao-carrinho

# 3. Cria os testes
# (trabalha nos arquivos...)

# 4. Verifica o que mudou
git status
git diff

# 5. Adiciona arquivos
git add test_carrinho.py
git add test_helpers.py

# 6. Commit
git commit -m "test: implementa testes de validação do carrinho"

# 7. Mais mudanças e commits...
git add .
git commit -m "test: adiciona cenários de carrinho vazio"

# 8. Envia para GitHub
git push -u origin test/validacao-carrinho

# 9. No GitHub, abre Pull Request

# 10. Após aprovação, volta para main
git checkout main
git pull

# 11. Deleta branch local
git branch -d test/validacao-carrinho
```

### Cenário 2: Corrigindo Bug Urgente

```bash
# 1. Você está trabalhando em algo, mas precisa parar
git stash save "WIP: teste de checkout em progresso"

# 2. Atualiza main
git checkout main
git pull

# 3. Cria branch para correção
git checkout -b hotfix/corrige-teste-login

# 4. Corrige o bug
# (edita arquivos...)

# 5. Commita
git add test_login.py
git commit -m "fix: corrige validação de senha no teste de login"

# 6. Envia
git push -u origin hotfix/corrige-teste-login

# 7. Merge direto ou via PR
git checkout main
git merge hotfix/corrige-teste-login
git push

# 8. Volta ao trabalho anterior
git checkout test/checkout
git stash pop
```

### Cenário 3: Colaborando com Equipe

```bash
# 1. Manhã: Atualiza antes de começar
git checkout main
git pull

# 2. Cria sua branch
git checkout -b test/api-pedidos

# 3. Trabalha e commita várias vezes
git add .
git commit -m "test: adiciona testes de API GET /pedidos"
# (mais trabalho...)
git add .
git commit -m "test: adiciona testes de API POST /pedidos"

# 4. Envia para GitHub
git push -u origin test/api-pedidos

# 5. Colega pede para você revisar código dele
git fetch origin
git checkout feature/teste-pagamento  # Branch do colega
# (revisa o código...)
git checkout test/api-pedidos  # Volta para sua branch

# 6. Alguém fez merge na main, você precisa atualizar
git checkout main
git pull
git checkout test/api-pedidos
git merge main  # Traz mudanças da main para sua branch

# 7. Resolve conflitos se houver (ver seção abaixo)

# 8. Push final
git push

# 9. Abre Pull Request no GitHub

# 10. Após aprovação
git checkout main
git pull
git branch -d test/api-pedidos
```

### Cenário 4: Trabalhando com Pull Requests

**No GitHub:**

1. Abra seu repositório
2. Clique em "Pull requests"
3. "New pull request"
4. Base: main, Compare: sua-branch
5. Preencha título e descrição
6. Adicione reviewers
7. "Create pull request"

**Após feedback:**

```bash
# Fazer mudanças solicitadas
git add .
git commit -m "refactor: aplica feedback da code review"
git push
# PR é atualizado automaticamente
```

**Após merge:**

```bash
git checkout main
git pull
git branch -d sua-branch
git push origin --delete sua-branch
```

---

## 🆘 Resolvendo Problemas

### Conflitos de Merge

**Quando acontece?**

Duas pessoas editaram a mesma linha do mesmo arquivo.

**Exemplo:**

```bash
git pull origin main
# Auto-merging test_login.py
# CONFLICT (content): Merge conflict in test_login.py
# Automatic merge failed; fix conflicts and then commit the result.
```

**Resolver o conflito:**

1. Abra o arquivo em conflito:

```python
def test_login():
<<<<<<< HEAD
    assert login_page.click_submit()
=======
    assert login_page.click_button()
>>>>>>> feature/api-tests
    assert login_page.verify_message()
```

2. Edite o arquivo, escolha qual versão manter (ou combine ambas):

```python
def test_login():
    assert login_page.click_submit()
    assert login_page.verify_message()
```

3. Remove os marcadores `<<<<<<<`, `=======`, `>>>>>>>`

4. Adicione e commite:

```bash
git add test_login.py
git commit -m "resolve: conflito no teste de login"
```

**Ver arquivos em conflito:**

```bash
git status
```

**Abortar merge:**

```bash
git merge --abort
```

Volta ao estado anterior ao merge.

### Recuperar Arquivo Deletado

**Arquivo deletado mas não commitado:**

```bash
git restore arquivo_deletado.py
```

**Arquivo deletado e commitado:**

```bash
git log --all --full-history -- arquivo_deletado.py
# Anota o hash do último commit que tinha o arquivo

git checkout a7b2c45 -- arquivo_deletado.py
git commit -m "recover: recupera arquivo_deletado.py"
```

### Desfazer Push (Perigoso!)

⚠️ **Só faça isso se NINGUÉM mais tiver baixado suas mudanças!**

```bash
git reset --hard HEAD~1
git push --force
```

**Alternativa mais segura (não apaga histórico):**

```bash
git revert HEAD
git push
```

### Mudei na Branch Errada

**Cenário:** Você fez mudanças na main em vez de criar uma branch.

**Solução 1: Stash + nova branch:**

```bash
git stash
git checkout -b feature/nova-funcionalidade
git stash pop
git add .
git commit -m "feat: adiciona nova funcionalidade"
```

**Solução 2: Commit + cherry-pick:**

```bash
git add .
git commit -m "feat: adiciona nova funcionalidade"
git log --oneline
# f3e8d12 Adiciona nova funcionalidade

git checkout -b feature/nova-funcionalidade
git reset --hard f3e8d12

git checkout main
git reset --hard HEAD~1
```

### Commitei Arquivo Sensível

**Remover do último commit:**

```bash
git rm --cached senha.txt
git commit --amend --no-edit
```

**Se já fez push:**

```bash
git rm --cached senha.txt
echo "senha.txt" >> .gitignore
git add .gitignore
git commit -m "remove: arquivo sensível"
git push
```

⚠️ **O arquivo ainda estará no histórico!** Para remover completamente:

```bash
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch senha.txt" \
  --prune-empty --tag-name-filter cat -- --all

git push --force --all
```

Ou use a ferramenta **BFG Repo-Cleaner**:

```bash
bfg --delete-files senha.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive
git push --force
```

### Branch Divergiu

```bash
git push
# error: failed to push some refs
# hint: Updates were rejected because the tip of your current branch is behind
```

**O que aconteceu:** Alguém fez push enquanto você trabalhava.

**Solução:**

```bash
git pull --rebase
git push
```

Ou:

```bash
git pull
# resolve conflitos se houver
git push
```

### Esqueci de Fazer Pull

**Situação:**

```bash
git add .
git commit -m "Meus testes"
git push
# error: failed to push
```

**Solução:**

```bash
git pull --rebase
# OU
git pull

# Resolve conflitos se houver
git push
```

---

## 🚨 Erros Comuns e Soluções

### Erro: "fatal: not a git repository"

**Causa:** Você não está dentro de uma pasta com Git inicializado.

**Solução:**

```bash
cd caminho/para/seu/projeto
git status  # Verifica se há repositório
# Se não houver:
git init
```

### Erro: "Permission denied (publickey)"

**Causa:** SSH não configurado corretamente.

**Solução:**

**Opção 1:** Use HTTPS em vez de SSH

```bash
git remote set-url origin https://github.com/usuario/repo.git
```

**Opção 2:** Configure SSH

```bash
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
cat ~/.ssh/id_ed25519.pub
# Copie a chave e adicione em GitHub → Settings → SSH and GPG keys
```

### Erro: "Your branch is ahead of 'origin/main' by X commits"

**Causa:** Você tem commits locais não enviados.

**Solução:**

```bash
git push
```

### Erro: "Please commit your changes or stash them before you merge"

**Causa:** Mudanças não salvas impedem troca de branch ou merge.

**Solução 1:** Commitar

```bash
git add .
git commit -m "work in progress"
```

**Solução 2:** Usar stash

```bash
git stash
git checkout outra-branch
git stash pop
```

### Erro: "CONFLICT (content): Merge conflict in arquivo.py"

**Causa:** Mesma linha editada em duas branches diferentes.

**Solução:**

1. Abra o arquivo
2. Procure por `<<<<<<<`, `=======`, `>>>>>>>`
3. Edite e escolha a versão correta
4. Remova os marcadores
5. `git add arquivo.py`
6. `git commit`

### Erro: "refusing to merge unrelated histories"

**Causa:** Tentando unir dois repositórios sem histórico comum.

**Solução:**

```bash
git pull origin main --allow-unrelated-histories
```

### Erro: "fatal: 'origin' does not appear to be a git repository"

**Causa:** Remote não configurado corretamente.

**Solução:**

```bash
git remote -v  # Verifica remotes
git remote add origin https://github.com/usuario/repo.git
```

### Erro: "You have divergent branches"

**Causa:** Históricos locais e remotos divergiram.

**Solução 1:** Rebase

```bash
git pull --rebase
```

**Solução 2:** Merge

```bash
git pull
git push
```

**Solução 3:** Forçar (cuidado!)

```bash
git push --force
```

### Erro: "filename too long"

**Causa:** Windows tem limite de 260 caracteres para caminhos.

**Solução:**

```bash
git config --system core.longpaths true
```

### Erro: "LF will be replaced by CRLF"

**Causa:** Diferenças de quebra de linha entre sistemas operacionais.

**Solução:**

**Windows:**

```bash
git config --global core.autocrlf true
```

**Linux/Mac:**

```bash
git config --global core.autocrlf input
```

### Recuperar Trabalho Perdido

**Commit foi deletado acidentalmente:**

```bash
git reflog
# Procure o commit perdido
git checkout commit-hash
```

Ou crie nova branch a partir dele:

```bash
git checkout -b recuperado commit-hash
```

**Branch deletada acidentalmente:**

```bash
git reflog
# Encontre o último commit da branch
git checkout -b branch-recuperada commit-hash
```

**Arquivo deletado acidentalmente:**

```bash
git checkout HEAD -- arquivo.py
```

**Mudanças descartadas com git restore:**

⚠️ Se você fez `git restore` sem commit, as mudanças foram perdidas permanentemente. Não há como recuperar.

**Dica:** Sempre commite trabalho importante antes de usar comandos destrutivos!

---

## ✅ Boas Práticas

### Commits

#### Faça commits pequenos e frequentes

❌ **Ruim:**

```bash
# Trabalha 2 dias inteiros
git add .
git commit -m "Fiz muita coisa"
```

✅ **Bom:**

```bash
git add test_login.py
git commit -m "test: adiciona teste de login com credenciais válidas"

git add test_login.py
git commit -m "test: adiciona teste de login com credenciais inválidas"

git add test_helpers.py
git commit -m "feat: cria helper para geração de usuários de teste"
```

#### Mensagens de commit claras

✅ **Padrão recomendado (Conventional Commits):**

```
tipo: Descrição curta (máximo 50 caracteres)

Descrição detalhada opcional (linha em branco antes)
Pode ter múltiplas linhas explicando o contexto
```

**Tipos comuns:**

- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `test`: Adiciona ou modifica testes
- `docs`: Documentação
- `refactor`: Refatoração de código
- `chore`: Tarefas de manutenção
- `style`: Formatação de código
- `perf`: Melhorias de performance
- `ci`: Mudanças em CI/CD

**Exemplos:**

```bash
git commit -m "test: adiciona validação de CPF no cadastro"
git commit -m "fix: corrige timeout no teste de checkout"
git commit -m "docs: atualiza README com instruções de execução"
git commit -m "refactor: simplifica lógica do helper de dados"
git commit -m "chore: atualiza dependências do projeto"
```

**Mensagem mais completa:**

```bash
git commit -m "test: implementa testes do fluxo de compra" -m "Cenários cobertos:
- Carrinho vazio
- Produto indisponível
- Cupom de desconto válido
- Cupom de desconto inválido
- Frete grátis
- Diferentes formas de pagamento"
```

### Branches

#### Nomes descritivos e padronizados

✅ **Bom:**

- `feature/testes-api-pedidos`
- `bugfix/corrige-validacao-email`
- `test/automacao-carrinho`
- `hotfix/falha-producao`
- `docs/instrucoes-setup`

❌ **Ruim:**

- `branch1`
- `nova-branch`
- `teste`
- `fix`
- `minha-branch`

#### Mantenha branches de vida curta

**Ideal:** 1-3 dias  
**Máximo:** 1 semana

**Processo:**

1. Crie a branch
2. Trabalhe nela
3. Faça merge
4. Delete a branch

Branches que vivem semanas/meses causam conflitos enormes.

#### Uma branch, uma funcionalidade

❌ **Não misture:**

```
feature/testes-login-e-checkout-e-api-e-docs
```

✅ **Separe:**

- `test/validacao-login`
- `test/fluxo-checkout`
- `test/endpoints-api`
- `docs/instrucoes-instalacao`

#### Delete branches após merge

```bash
git branch -d feature/teste-concluido
git push origin --delete feature/teste-concluido
```

Mantenha repositório limpo!

### Pull Requests

#### Sempre faça pull antes de começar

Início do dia ou início de nova tarefa:

```bash
git checkout main
git pull
```

#### Revise seu código antes de criar PR

```bash
git diff main..sua-branch
```

**Verifique:**

- ✅ Sem código comentado desnecessário
- ✅ Sem TODOs esquecidos
- ✅ Sem `console.log()` ou `print()` de debug
- ✅ Sem arquivos de configuração local

#### Descreva bem o PR

**Título:**

```
test: implementa testes do fluxo de checkout
```

**Descrição:**

```markdown
## O que foi feito

Implementa testes automatizados do fluxo de checkout

## Cenários cobertos

- Checkout com carrinho vazio
- Checkout com produto indisponível
- Checkout com cupom de desconto válido
- Checkout com cupom de desconto inválido
- Checkout com diferentes formas de pagamento

## Como testar

1. Execute `pytest tests/test_checkout.py`
2. Verifique os relatórios em `reports/`

## Checklist

- [x] Testes passando
- [x] Código revisado
- [x] Documentação atualizada
- [ ] Code review aprovado
```

#### Seja um bom revisor

Ao revisar PR de colegas:

- ✅ Seja construtivo, não crítico
- ✅ Elogie o que está bom
- ✅ Sugira melhorias
- ✅ Teste o código localmente

**Comentários úteis:**

- ✅ "Boa abordagem! Considere adicionar um teste para o cenário X"
- ✅ "Funcionou bem. Que tal extrair essa lógica para um helper?"

**Comentários ruins:**

- ❌ "Está errado"
- ❌ "Não entendi nada"

### Segurança

#### NUNCA commite:

- ❌ Senhas
- ❌ Tokens de API
- ❌ Chaves privadas
- ❌ Arquivos `.env` com credenciais
- ❌ Configurações de produção
- ❌ Dados pessoais de clientes/usuários

#### Use .gitignore sempre

Crie logo no início do projeto.

**Exemplo básico:**

```
.env
.env.local
config_local.json
*.key
*.pem
secrets/
credentials/
```

#### Revise antes de commitar

```bash
git diff
```

Confira linha por linha antes de `git add`.

**Dica:** Use `git add -p` para revisar cada mudança:

```bash
git add -p test_login.py
```

Git mostra cada bloco de mudança e pergunta:

```
Stage this hunk [y,n,q,a,d,e,?]?
y = sim
n = não
q = sair
a = todos
d = nenhum
```

#### Use variáveis de ambiente

❌ **Ruim:**

```python
API_TOKEN = "abc123xyz"
```

✅ **Bom:**

```python
import os
API_TOKEN = os.getenv("API_TOKEN")
```

**Arquivo `.env` (não commitado):**

```
API_TOKEN=abc123xyz
```

**Arquivo `.env.example` (commitado):**

```
API_TOKEN=seu_token_aqui
```

### Organização

#### Estrutura de pastas clara

```
projeto-testes/
├── .gitignore
├── README.md
├── requirements.txt
├── setup.py
├── tests/
│   ├── unit/
│   │   ├── test_validators.py
│   │   └── test_helpers.py
│   ├── integration/
│   │   ├── test_api.py
│   │   └── test_database.py
│   ├── e2e/
│   │   ├── test_login.py
│   │   ├── test_checkout.py
│   │   └── test_search.py
│   └── conftest.py
├── helpers/
│   ├── data_helpers.py
│   ├── api_helpers.py
│   └── page_objects.py
├── config/
│   ├── config.json
│   └── config.example.json
├── data/
│   ├── test_users.json
│   └── test_products.json
├── fixtures/
│   └── sample_data.py
└── reports/  (ignorado no .gitignore)
```

#### README.md completo

```markdown
# Projeto de Testes Automatizados

## Descrição

Testes automatizados do sistema XYZ

## Pré-requisitos

- Python 3.11+
- pip
- Chrome/Firefox

## Instalação

```bash
git clone https://github.com/empresa/projeto-testes.git
cd projeto-testes
pip install -r requirements.txt
```

## Configuração

1. Copie `config.example.json` para `config.json`
2. Configure as credenciais de teste
3. Configure a URL base do ambiente

## Executar Testes

**Todos os testes:**

```bash
pytest
```

**Testes específicos:**

```bash
pytest tests/e2e/test_login.py
```

**Com relatório HTML:**

```bash
pytest --html=report.html
```

## Estrutura

- `tests/unit/` - Testes unitários
- `tests/integration/` - Testes de integração
- `tests/e2e/` - Testes end-to-end

Contribuindo

1. Crie uma branch (`git checkout -b test/nova-funcionalidade`)
2. Commit suas mudanças (`git commit -m 'test: adiciona novo teste'`)
3. Push para a branch (`git push origin test/nova-funcionalidade`)
4. Abra um Pull Request
```

Documente decisões importantes

Use commits para documentar "por quê":

❌ `git commit -m "mudança"`

✅ `git commit -m "test: remove validação de CPF temporariamente" -m "API de validação está fora do ar. Ticket: JIRA-123"`

Mantenha histórico limpo

Evite commits de merge desnecessários:

Use `git pull --rebase` em vez de `git pull`

Combine commits relacionados antes de PR:


git rebase -i HEAD~3
```

Evite commits de "fix typo":

Use `git commit --amend` se ainda não fez push

### Trabalho em Equipe

#### Comunique-se

**Antes de grandes mudanças:**

- Avise a equipe
- Abra uma issue ou discussion
- Peça feedback

**Ao encontrar problemas:**

- Documente no commit/PR
- Crie issue se necessário
- Comunique em Slack/Teams

#### Sincronize frequentemente

```bash
git pull origin main
```

Faça isso várias vezes ao dia, especialmente antes de:

- Começar novo trabalho
- Fazer merge
- Abrir PR

#### Respeite o trabalho dos outros

**Não force push em branches compartilhadas:**

```bash
git push --force  # ⚠️ Perigoso!
```

**Não reescreva histórico público:**

`git rebase` em branches já no GitHub pode causar problemas

**Se precisar fazer force push, avise a equipe!**

#### Automatização

- Use pre-commit hooks para validação automática
- Use CI/CD para rodar testes
- Configure notificações de build
- Automatize geração de relatórios

---

## 📖 Glossário de Termos

| Termo | Significado |
|-------|-------------|
| **Repository (Repo)** | Projeto versionado pelo Git |
| **Commit** | Snapshot do código em um momento específico |
| **Branch** | Linha de desenvolvimento paralela |
| **Merge** | Unir duas branches |
| **Pull Request (PR)** | Solicitação de revisão de código antes de merge |
| **Fork** | Cópia de repositório para sua conta |
| **Clone** | Baixar repositório remoto para máquina local |
| **Remote** | Repositório hospedado online (GitHub, GitLab) |
| **Origin** | Nome padrão do repositório remoto principal |
| **Upstream** | Repositório original quando você fez fork |
| **HEAD** | Ponteiro para o commit atual |
| **Staging Area** | Área de preparação para commit |
| **Working Directory** | Arquivos que você está editando |
| **Tracked Files** | Arquivos que Git está monitorando |
| **Untracked Files** | Arquivos novos que Git ainda não conhece |
| **Conflict** | Quando mesma linha foi editada em branches diferentes |
| **Stash** | Salvar mudanças temporariamente sem commit |
| **Cherry-pick** | Copiar commit específico para outra branch |
| **Rebase** | Reescrever histórico de commits |
| **Reset** | Voltar para commit anterior |
| **Revert** | Criar novo commit que desfaz mudanças |
| **Tag** | Marcador de versão específica |
| **SHA/Hash** | Identificador único do commit (ex: a7b2c45) |
| **Fast-forward** | Merge simples quando não há divergência |
| **Three-way merge** | Merge quando há commits em ambas branches |
| **Detached HEAD** | Estado quando HEAD aponta para commit específico, não branch |
| **.gitignore** | Arquivo que lista o que não versionar |
| **README** | Arquivo de documentação do projeto |
| **Push** | Enviar commits locais para repositório remoto |
| **Pull** | Baixar e aplicar mudanças do remoto |
| **Fetch** | Baixar mudanças sem aplicar |
| **Diff** | Diferenças entre versões |
| **Blame** | Ver quem modificou cada linha |
| **Log** | Histórico de commits |
| **Reflog** | Histórico de todas as ações no repositório |
| **Hook** | Script que executa automaticamente em eventos Git |
| **CI/CD** | Integração e Deploy Contínuos |
| **GitFlow** | Modelo de branching estruturado |
| **Trunk-based** | Modelo onde todos trabalham em branch principal |
| **Squash** | Combinar múltiplos commits em um |
| **Amend** | Modificar último commit |
| **WIP** | Work In Progress (trabalho em andamento) |

---

## 🎨 Templates .gitignore por Framework

### Python / Pytest

```
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg

# Virtual Environment
venv/
env/
ENV/
.venv

# Pytest
.pytest_cache/
.coverage
htmlcov/
.tox/
.cache

# Relatórios
reports/
screenshots/
*.log
*.xml
*.html

# IDE
.vscode/
.idea/
*.swp
*.swo
*~

# Configurações locais
.env
.env.local
config_local.py
secrets.json

# OS
.DS_Store
Thumbs.db
```

### JavaScript / Cypress / Playwright

```
# Node
node_modules/
npm-debug.log
yarn-error.log
package-lock.json
yarn.lock

# Cypress
cypress/videos/
cypress/screenshots/
cypress/downloads/

# Playwright
test-results/
playwright-report/
playwright/.cache/

# Relatórios
reports/
coverage/
.nyc_output/

# Logs
*.log
logs/

# IDE
.vscode/
.idea/

# Configurações
.env
.env.local
.env.test

# OS
.DS_Store
Thumbs.db
```

### Java / Selenium

```
# Compiled
*.class
*.jar
*.war
*.ear
target/
build/
out/

# Maven
.mvn/
mvnw
mvnw.cmd

# Gradle
.gradle/
gradle/
gradlew
gradlew.bat

# IDE
.idea/
*.iml
.classpath
.project
.settings/
*.swp

# Selenium
drivers/
screenshots/
logs/
*.log

# Relatórios
test-output/
allure-results/
allure-report/

# OS
.DS_Store
Thumbs.db
```

### Robot Framework

```
# Robot Framework
log.html
output.xml
report.html
selenium-screenshot-*.png
*.png
*.log

# Python
__pycache__/
*.pyc
venv/

# Relatórios
results/
reports/
screenshots/

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db
```

### Postman / API Testing

```
# Newman
newman/

# Relatórios
reports/
*.html
*.xml

# Logs
*.log

# Configurações
.env
environment.json
secrets.json

# OS
.DS_Store
Thumbs.db
```

### Template Universal para Projetos de Teste

```
# LOGS E RELATÓRIOS
logs/
reports/
*.log
*.html
*.xml
allure-results/
allure-report/
test-output/
coverage/
htmlcov/
.nyc_output/

# SCREENSHOTS E EVIDÊNCIAS
screenshots/
videos/
evidence/
*.png
*.jpg
*.gif
*.mp4

# DRIVERS E BINÁRIOS
drivers/
*.exe
chromedriver
geckodriver
msedgedriver

# AMBIENTES VIRTUAIS
venv/
env/
.venv/
node_modules/

# CACHE
__pycache__/
*.pyc
*.pyo
.pytest_cache/
.cache/
.gradle/
.mvn/

# BUILDS
build/
dist/
target/
out/

# CONFIGURAÇÕES SENSÍVEIS
.env
.env.local
.env.test
config_local.*
secrets.*
credentials.*
*.key
*.pem

# IDE
.vscode/
.idea/
*.swp
*.swo
*~
.classpath
.project
.settings/

# SISTEMA OPERACIONAL
.DS_Store
Thumbs.db
desktop.ini

# TEMPORÁRIOS
*.tmp
*.temp
*.bak
~$*
```

---

## 🧠 Quiz de Autoavaliação

### Nível Básico

**1. Qual comando inicializa um repositório Git?**

a) `git start`  
b) `git init`  
c) `git create`  
d) `git new`

**2. Como ver o status atual dos arquivos?**

a) `git status`  
b) `git show`  
c) `git info`  
d) `git check`

**3. Qual a diferença entre `git add` e `git commit`?**

a) São a mesma coisa  
b) add prepara, commit salva no histórico  
c) add salva, commit envia para GitHub  
d) Não há diferença

**4. Como adicionar todos os arquivos modificados?**

a) `git add all`  
b) `git add *`  
c) `git add .`  
d) `git add everything`

**5. Qual comando mostra o histórico de commits?**

a) `git history`  
b) `git log`  
c) `git commits`  
d) `git show`

### Nível Intermediário

**6. Como criar e mudar para uma nova branch ao mesmo tempo?**

a) `git branch -n nova-branch`  
b) `git checkout -b nova-branch`  
c) `git create nova-branch`  
d) `git switch nova-branch`

**7. O que fazer quando `git push` é rejeitado?**

a) `git push --force`  
b) `git pull` primeiro  
c) Criar nova branch  
d) Deletar o repositório

**8. Como desfazer o último commit mantendo as mudanças?**

a) `git reset --hard HEAD~1`  
b) `git reset --soft HEAD~1`  
c) `git revert HEAD`  
d) `git undo`

**9. Qual a diferença entre `git fetch` e `git pull`?**

a) São iguais  
b) fetch baixa, pull baixa e aplica  
c) pull é mais rápido  
d) fetch é obsoleto

**10. Como salvar mudanças temporariamente sem commit?**

a) `git save`  
b) `git temp`  
c) `git stash`  
d) `git hold`

### Nível Avançado

**11. Quando usar `git rebase` em vez de `git merge`?**

a) Sempre usar rebase  
b) Rebase para histórico linear  
c) Nunca usar rebase  
d) São a mesma coisa

**12. Como recuperar um commit que foi deletado?**

a) Impossível recuperar  
b) `git reflog` + `git checkout`  
c) `git restore`  
d) `git undo delete`

**13. Explique a diferença entre reset --soft, --mixed e --hard**

a) São iguais  
b) soft (staging), mixed (working), hard (apaga)  
c) Apenas sintaxe diferente  
d) hard é mais seguro

**14. O que é cherry-pick e quando usar?**

a) Deletar commits  
b) Copiar commit específico para outra branch  
c) Merge automático  
d) Comando obsoleto

**15. Como compartilhar Git Hooks com a equipe?**

a) Impossível, hooks são locais  
b) Criar pasta hooks/ versionada  
c) GitHub faz automaticamente  
d) Não é necessário

### Respostas

**Nível Básico:**
1. b) git init
2. a) git status
3. b) add prepara, commit salva no histórico
4. c) git add .
5. b) git log

**Nível Intermediário:**
6. b) git checkout -b nova-branch
7. b) git pull primeiro
8. b) git reset --soft HEAD~1
9. b) fetch baixa, pull baixa e aplica
10. c) git stash

**Nível Avançado:**
11. b) Rebase para histórico linear
12. b) git reflog + git checkout
13. b) soft (staging), mixed (working), hard (apaga)
14. b) Copiar commit específico para outra branch
15. b) Criar pasta hooks/ versionada

### Sua Pontuação:

- **0-5:** Iniciante - Continue estudando os conceitos básicos
- **6-10:** Intermediário - Você está no caminho certo!
- **11-13:** Avançado - Ótimo conhecimento!
- **14-15:** Expert - Parabéns, você domina Git!

---

## 📋 Cheat Sheet

### Configuração

```bash
git config --global user.name "Nome"
git config --global user.email "email@exemplo.com"
git config --list
```

### Básico

```bash
git init                                           # Iniciar repositório
git status                                         # Ver status
git add arquivo.py                                 # Adicionar arquivo
git add .                                          # Adicionar todos
git commit -m "mensagem"                           # Commitar
git log                                            # Ver histórico
git log --oneline                                  # Histórico resumido
git log --graph --all                              # Gráfico de branches
```

### Desfazer

```bash
git restore arquivo                                # Descartar mudanças
git restore --staged arquivo                       # Tirar da staging
git reset --soft HEAD~1                            # Desfazer commit (mantém mudanças)
git reset --mixed HEAD~1                           # Desfazer commit (working directory)
git reset --hard HEAD~1                            # Desfazer commit (apaga tudo)
git revert hash                                    # Reverter commit
git commit --amend                                 # Modificar último commit
```

### Branches

```bash
git branch                                         # Listar branches
git branch nome-branch                             # Criar branch
git checkout nome-branch                           # Trocar de branch
git checkout -b nome-branch                        # Criar e trocar
git merge nome-branch                              # Fazer merge
git branch -d nome-branch                          # Deletar branch
git branch -D nome-branch                          # Forçar deleção
```

### Remoto

```bash
git clone url                                      # Clonar repositório
git remote add origin url                          # Conectar com remoto
git remote -v                                      # Ver remotos
git push origin main                               # Enviar para GitHub
git pull origin main                               # Baixar do GitHub
git fetch origin                                   # Baixar sem merge
git push -u origin branch                          # Push e configurar tracking
```

### Stash

```bash
git stash                                          # Salvar temporariamente
git stash list                                     # Listar stashes
git stash pop                                      # Recuperar e remover
git stash apply                                    # Recuperar sem remover
git stash drop                                     # Deletar stash
git stash clear                                    # Deletar todos stashes
```

### Avançado

```bash
git diff                                           # Ver diferenças
git diff --staged                                  # Ver staged
git diff branch1..branch2                          # Comparar branches
git grep "texto"                                   # Procurar no código
git blame arquivo                                  # Ver quem editou
git tag v1.0                                       # Criar tag
git tag -a v1.0 -m "msg"                          # Tag anotada
git push origin --tags                             # Enviar tags
git cherry-pick hash                               # Copiar commit
git rebase branch                                  # Rebase
git reflog                                         # Ver histórico completo
```

### Conflitos

```bash
git status                                         # Ver arquivos em conflito
# Editar arquivo, remover marcadores <<<<< ===== >>>>>
git add arquivo                                    # Marcar como resolvido
git commit                                         # Finalizar merge
git merge --abort                                  # Cancelar merge
```

### Limpeza

```bash
git clean -n                                       # Ver o que seria deletado
git clean -f                                       # Deletar arquivos untracked
git clean -fd                                      # Deletar arquivos e pastas
git gc                                             # Garbage collection
git prune                                          # Remover objetos inacessíveis
```

---

## 📚 Recursos Adicionais

### Documentação Oficial

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com)
- [Git Book (Português)](https://git-scm.com/book/pt-br/v2)
- [GitHub Skills](https://skills.github.com)

### Tutoriais Interativos

- [Learn Git Branching](https://learngitbranching.js.org)
- [Git Immersion](https://gitimmersion.com)
- [GitHub Learning Lab](https://lab.github.com)
- [Codecademy Git](https://www.codecademy.com/learn/learn-git)

### Ferramentas Visuais

- [GitKraken](https://www.gitkraken.com)
- [SourceTree](https://www.sourcetreeapp.com)
- [GitHub Desktop](https://desktop.github.com)
- [Git Extensions](https://gitextensions.github.io)
- [Fork](https://git-fork.com)

### Jogos e Desafios

- [Oh My Git!](https://ohmygit.org)
- [Git Game](https://github.com/git-game/git-game)
- [Git Kata](https://github.com/eficode-academy/git-katas)
- [Git Gud](https://github.com/benthayer/git-gud)

### Vídeos e Cursos

- Git e GitHub para Iniciantes - Willian Justen (YouTube)
- Curso Git - Código Fonte TV (YouTube)
- Git Tutorial - freeCodeCamp (YouTube)
- Git & GitHub Crash Course - Traversy Media (YouTube)

### Comunidades

- [Stack Overflow - Git](https://stackoverflow.com/questions/tagged/git)
- [Reddit - r/git](https://www.reddit.com/r/git)
- [Dev.to - Git](https://dev.to/t/git)
- Discord - Git Together

### Livros Recomendados

- **Pro Git** - Scott Chacon (gratuito online)
- **Version Control with Git** - Jon Loeliger
- **Git Pocket Guide** - Richard E. Silverman

### Blogs e Artigos

- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Blog](https://github.blog)
- Git Better

### Ferramentas Úteis

- [Hub](https://hub.github.com) - CLI do GitHub
- [Lazygit](https://github.com/jesseduffield/lazygit) - Terminal UI
- [Tig](https://jonas.github.io/tig) - Text-mode interface
- [Git-extras](https://github.com/tj/git-extras) - Comandos extras
- [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner) - Limpar histórico

---

## 🤝 Contribuindo com Este Guia

Este guia é vivo e colaborativo. Sua contribuição pode ajudar centenas de QAs!

### Como Contribuir

- 🐛 Encontrou erro? Abra uma issue
- 💡 Tem sugestão? Abra uma issue ou discussion
- ✨ Quer adicionar conteúdo? Envie um Pull Request
- 🌍 Quer traduzir? Entre em contato

### Tipos de Contribuição Aceitas

✅ Correções de erros e typos  
✅ Novos exemplos práticos  
✅ Melhorias nas explicações  
✅ Traduções para outros idiomas  
✅ Exercícios adicionais  
✅ Casos de uso reais  
✅ Melhorias na formatação  
✅ Adição de diagramas e imagens

### Processo de Contribuição

```bash
# 1. Fork este repositório no GitHub

# 2. Clone seu fork
git clone https://github.com/SEU-USUARIO/git-para-qa.git
cd git-para-qa

# 3. Crie uma branch descritiva
git checkout -b melhoria/adiciona-exemplo-hooks

# 4. Faça suas alterações
# Edite os arquivos...

# 5. Commit com mensagem descritiva
git add .
git commit -m "docs: adiciona exemplos de Git Hooks para automação"

# 6. Push para seu fork
git push origin melhoria/adiciona-exemplo-hooks

# 7. Abra Pull Request no repositório original
# Descreva suas mudanças
# Explique por que é útil
# Adicione screenshots se relevante
```

### Diretrizes de Contribuição

**Mensagens de Commit:**

Use Conventional Commits:
- `docs:` para documentação
- `fix:` para correções
- `feat:` para novas funcionalidades
- `style:` para formatação

**Código de Conduta:**

- Seja respeitoso e construtivo
- Critique ideias, não pessoas
- Ajude outros a crescer
- Celebre contribuições

**Estilo de Escrita:**

- Use linguagem clara e acessível
- Evite jargões desnecessários
- Prefira exemplos práticos
- Use emojis para destacar seções importantes

**Revisão:**

- Todas as contribuições serão revisadas
- Feedback construtivo será fornecido
- Alterações podem ser solicitadas
- Agradecimento por toda contribuição!

---

## ⭐ Como Apoiar Este Projeto

Achou útil? Existem várias formas de apoiar:

⭐ Dê uma estrela no repositório GitHub  
🔄 Compartilhe nas redes sociais (LinkedIn, Twitter, Reddit)  
💬 Deixe feedback (issues ou discussions)  
🤝 Contribua com melhorias ou traduções  
📢 Indique para sua equipe e comunidade de QA  
✍️ Escreva sobre o guia no seu blog ou Medium  
🎓 Use em treinamentos e workshops  
🌟 Faça fork e personalize para sua empresa

Quanto mais pessoas usarem, melhor o guia fica!

---

### Conte-nos:

✅ Este guia te ajudou?  
✅ O que você mais gostou?  
✅ O que poderia melhorar?  
✅ Que conteúdo gostaria de ver adicionado?  
✅ Encontrou algum erro ou informação desatualizada?


---

## 🎬 Conclusão

Parabéns por chegar até aqui! 🎉

### Você agora tem conhecimento completo sobre:

✅ Fundamentos do Git  
✅ Versionamento de código  
✅ Trabalho com branches  
✅ Colaboração no GitHub  
✅ Resolução de conflitos  
✅ Git Hooks e automação  
✅ Integração CI/CD  
✅ GitFlow e workflows  
✅ Casos de uso avançados para QA

### O que fazer agora?

**1. Pratique Diariamente**

- Use Git em todos os seus projetos de teste
- Faça commits frequentes e bem descritos
- Experimente comandos novos

**2. Ensine Outros**

- A melhor forma de consolidar conhecimento
- Ajude colegas iniciantes
- Compartilhe este guia

**3. Contribua**

- Participe de projetos open-source
- Contribua com este guia
- Compartilhe casos de uso reais

**4. Continue Aprendendo**

- Git é vasto, sempre há mais a aprender
- Explore comandos avançados
- Acompanhe atualizações do Git

**5. Automatize**

- Configure hooks para seu fluxo
- Integre com CI/CD
- Otimize processos da equipe

### Lembre-se:

> "Git é como um superpoder para QAs. Depois que dominar, você nunca mais vai querer trabalhar sem versionamento."

> "A melhor forma de aprender Git é usando Git. Não tenha medo de errar - em repositórios de teste, você pode fazer qualquer coisa!"

> "Commits frequentes salvam vidas (e projetos)."

### Próximos Passos Recomendados:

- [ ] Crie seu primeiro repositório de testes hoje
- [ ] Use Git diariamente durante próximo mês
- [ ] Complete todos os desafios práticos
- [ ] Ajude 3 colegas a começar com Git
- [ ] Contribua com 1 projeto open-source
- [ ] Compartilhe este guia com sua equipe

### Obrigado por usar este guia! 🙏

Se ajudou você, ajudará outros QAs também. **Compartilhe!** ⭐

---

**Feito com ☕, 💻 e muito ❤️ por QAs para QAs**


---

⭐ **Se este guia ajudou você, considere dar uma estrela no GitHub!**

🔄 **Compartilhe com outros QAs que querem aprender Git!**

🤝 **Contribuições são sempre bem-vindas!**

**Vamos juntos tornar o mundo QA melhor, um commit por vez!** 🚀

---
