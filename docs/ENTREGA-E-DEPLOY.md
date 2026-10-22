# Publicação e fluxo Git — passo a passo

## 1. Preparar os arquivos

Extraia o ZIP. Abra a pasta orbe-startup no VS Code (a que contém index.html). Abra Terminal > Novo terminal. Você pode visualizar o resultado abrindo index.html.

Não faça um único git add . no início: o roteiro abaixo separa a integração dos arquivos prontos por branches. Revise cada grupo antes de commitá-lo; a sequência registra a integração do material recebido, não um histórico fictício de autoria.

## 2. Criar um repositório novo no GitHub

Na sua conta belaSimoes, crie um repositório público chamado orbe-startup, sem gerar README, licença ou gitignore. Se esse nome já existir, escolha outro e substitua o nome nos comandos. Não execute git init dentro de outro projeto existente.

## 3. Inicializar e separar o trabalho em branches

Execute os blocos abaixo em ordem, na pasta extraída. Pare se um comando falhar.

### Base na main

```bash
git init -b main
git add README.md .gitignore .nojekyll
git commit -m "Inicia o projeto Orbe e documenta a proposta"
```

Se o Git pedir identidade, configure com seu nome e e-mail associado ao GitHub (ou endereço noreply da conta):

```bash
git config user.name "Isabela Cruz Simões"
git config user.email "SEU_EMAIL_DO_GITHUB"
```

Substitua o e-mail antes de executar e repita o commit.

### Planejamento

Mova ORB-01 para Em andamento, revise a documentação e execute:

```bash
git switch -c docs/planejamento
git add docs
git commit -m "Organiza backlog, sprint, Kanban e roteiro de entrega"
git switch main
git merge --no-ff docs/planejamento -m "Integra o planejamento do projeto"
```

### Estrutura HTML

```bash
git switch -c feat/estrutura
git add index.html assets
git commit -m "Adiciona a estrutura e o conteudo do site"
git switch main
git merge --no-ff feat/estrutura -m "Integra a estrutura da pagina"
```

### Estilos

```bash
git switch -c feat/visual
git add style.css
git commit -m "Adiciona identidade visual e layout responsivo"
git switch main
git merge --no-ff feat/visual -m "Integra os estilos do site"
```

### Interatividade

```bash
git switch -c feat/kanban
git add script.js
git commit -m "Adiciona Kanban com persistencia local"
git switch main
git merge --no-ff feat/kanban -m "Integra a demonstracao funcional"
```

Para cada tarefa, use Em revisão ao conferir e Concluído depois de cumprir o aceite. O --no-ff preserva um commit explícito de integração, permitindo mostrar o uso de branches.

### Conferir e enviar

```bash
git status
git log --oneline --graph --all
git remote add origin https://github.com/belaSimoes/orbe-startup.git
git push -u origin main
git push origin docs/planejamento feat/estrutura feat/visual feat/kanban
```

Se solicitado, autentique-se na sua conta pelo fluxo oferecido pelo Git. Não use a senha da conta como senha de Git por HTTPS; use o gerenciador de credenciais ou token quando necessário. Não coloque tokens no código ou no README.

## 4. Hospedar no GitHub Pages

1. Abra o repositório no GitHub.
2. Vá em Settings > Pages.
3. Em Build and deployment, selecione Source: Deploy from a branch.
4. Em Branch, escolha main e /(root).
5. Clique em Save.
6. Aguarde a publicação. A aba Actions mostra o andamento do processo.
7. Abra a URL exibida em Pages. Com o usuário e nome sugeridos, será https://belasimoes.github.io/orbe-startup/ . Só considere publicada quando a página abrir corretamente.

O index.html precisa estar na raiz do repositório, não dentro de uma segunda pasta orbe-startup. Os caminhos dos assets são relativos, compatíveis com o subdiretório do GitHub Pages. Não há backend para hospedar.

## 5. Revisão e entrega

Execute docs/VALIDACAO.md. Para corrigir algo, crie uma branch fix/revisao, altere os arquivos, faça o commit e integre na main com merge. Se não houver defeito, não crie commits de correção vazios.

Depois de validar e publicar, crie a branch docs/entrega, registre no README a URL real publicada, complete a validação e a retrospectiva, faça o commit, integre na main e envie o resultado. Não marque o deploy como concluído antes de verificar.

Entregue:
- Link do repositório.
- Link do site publicado.
- Link do quadro GitHub Projects (configure acesso para o professor visualizar).
- Prints do quadro, histórico de branches/commits e site funcionando, caso sejam solicitados.
- Documentação de planejamento e validação no repositório.

## Fontes

https://docs.github.com/pt/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
https://docs.github.com/en/issues/planning-and-tracking-with-projects

O código foi preparado para publicação. Nenhum repositório ou site foi publicado automaticamente na sua conta.
