# 📚 Git para QA

Guia prático demonstrando como **Analistas de Qualidade (QA)** utilizam **Git e GitHub** no dia a dia para versionar testes, documentações e colaborar com times de desenvolvimento.

---

## 🎯 Objetivo

Mostrar a aplicação de Git em atividades reais de QA, como:

- Versionamento de scripts de teste
- Organização de casos de teste
- Controle de mudanças em automação
- Colaboração com desenvolvedores
- Registro de evidências e relatórios de teste

---

## 🧪 Exemplos de Uso do Git em QA

### 📌 1. Versionando scripts de teste

```bash
git add tests/test_login.py
git commit -m "test: adiciona teste de login com credenciais válidas"

Permite rastrear alterações e evolução dos testes.


🌿 2. Trabalhando com branches para novas funcionalidades

git checkout -b feature/testes-carrinho
git add tests/test_carrinho.py
git commit -m "test: adiciona cenários de teste do carrinho de compras"
git push origin feature/testes-carrinho

Isola o trabalho de testes para novas funcionalidades.



🛠️ 3. Correção de testes quebrados

git checkout -b fix/ajuste-teste-login
git commit -m "fix: ajusta seletor após mudança na tela de login"

Mantém histórico claro de correções.



📄 4. Documentação de casos de teste

git add casos-de-teste/CT-001-login.md
git commit -m "docs: adiciona caso de teste para validação de login"

Ajuda a manter documentação versionada e organizada.



📊 5. Versionando relatórios de teste

git add relatorios/sprint-10-resultados.md
git commit -m "docs: adiciona relatório de execução da sprint 10"

Garante histórico de execuções e rastreabilidade.




🛠️ Ferramentas Utilizadas

Git

GitHub




📌 O que este projeto demonstra

✔ Uso de Git aplicado à rotina de QA
✔ Organização de testes e documentações com versionamento
✔ Boas práticas de mensagens de commit
✔ Trabalho com branches para novas features e correções



🚧 Próximos Passos

Adicionar exemplos de resolução de conflitos

Demonstrar fluxo de Pull Request

Integrar testes automatizados com versionamento
