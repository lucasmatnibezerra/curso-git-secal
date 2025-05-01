
# Atividade de Git: Colaboração em Equipe (via Fork)

Este documento descreve as instruções que cada aluno deve seguir para realizar uma atividade prática de colaboração utilizando Git e GitHub.  
A atividade tem como objetivo ensinar os fundamentos de versionamento distribuído e simular um fluxo de colaboração real com uso de branches, commits e pull requests **via fork**, o método mais utilizado em projetos públicos.

## Objetivo da Atividade

Você irá:

- Fazer um fork de um repositório remoto hospedado no GitHub.
- Clonar o repositório forkado para sua máquina.
- Criar uma branch individual com seu nome.
- Adicionar seu nome ao arquivo equipe.txt.
- Cometer (commit) suas alterações com uma mensagem descritiva.
- Enviar sua branch para o seu repositório no GitHub (push).
- Criar um pull request para que sua contribuição seja integrada ao repositório original do professor.

---

## Pré-requisitos

Antes de iniciar a atividade, você deve ter:

1. Git instalado na sua máquina. Verifique com:
   ```
   git --version
   ```

2. Uma conta no GitHub e estar logado em um navegador.

3. Acesso ao repositório original:  
   https://github.com/lucasmatnibezerra/curso-git-secal

---

## Passo a Passo

### 1. Faça um fork do repositório

1. Acesse o repositório original do professor:  
   https://github.com/lucasmatnibezerra/curso-git-secal

2. No canto superior direito da página, clique no botão **"Fork"**.

3. O GitHub criará uma cópia do repositório no seu próprio perfil.

---

### 2. Clone o seu fork

No terminal, execute o comando abaixo (substitua com o link do seu fork):

```
git clone https://github.com/seu-usuario/curso-git-secal.git
cd curso-git-secal
```

---

### 3. Crie uma branch com seu nome

Você deve criar uma branch nova para trabalhar isoladamente. A branch deve ter seu nome (sem espaços, tudo minúsculo, de preferência).

```
git checkout -b seu-nome
```

Exemplo:

```
git checkout -b lucasmatnibezerra
```

---

### 4. Edite o arquivo equipe.txt

Abra o arquivo `equipe.txt` com o seu editor de texto preferido.

Adicione seu nome ao final da lista no arquivo. Por exemplo:

```
Lista de integrantes do projeto:
- Lucas Matni Bezerra
```

Salve o arquivo.

---

### 5. Adicione e comite as alterações

```bash
git add equipe.txt
git commit -m "Adiciona Lucas Matni Bezerra à lista de integrantes"
```

---

### 6. Envie sua branch para o seu fork no GitHub

```bash
git push origin lucasmatnibezerra
```

Substitua `lucasmatnibezerra` pelo nome da sua branch.

---

### 7. Crie um Pull Request para o repositório original

1. Acesse o seu repositório no GitHub.

2. O GitHub mostrará uma opção para criar um pull request para o repositório original (lucasmatnibezerra/curso-git-secal).

3. Clique em **"Compare & pull request"**.

4. Verifique o título e escreva uma descrição, como:
   > Adicionando Lucas Matni Bezerra à lista de integrantes.

5. Clique em **"Create pull request"**.

---

### 8. Aguardar a análise

O professor (Lucas Matni) fará a análise e o merge da sua contribuição ao repositório original.

---

## Considerações Finais

- Nunca edite diretamente a branch `main` do repositório original.
- Use sempre sua própria branch e repositório.
- Após o merge, você pode atualizar seu fork com:

```bash
git remote add upstream https://github.com/lucasmatnibezerra/curso-git-secal.git
git fetch upstream
git merge upstream/main
```

---

## Dúvidas

Essa atividade é feita para praticar em grupo, e dúvidas fazem parte do processo de aprendizagem.  
Se tiver problemas com fork, push, ou pull request, fale com o professor.
---

# Atividade Avançada de Git: Projeto de Desenvolvimento em Camadas

Esta atividade foi elaborada para praticar o uso mais completo do Git de forma individual. Você irá simular um fluxo de trabalho profissional, com foco em criação de branches, commits frequentes e significativos, visualização de histórico, resolução de conflitos e boa organização do repositório.

## Objetivo

Nesta atividade, você irá desenvolver um pequeno projeto de texto ou código em etapas. A cada etapa, você aplicará comandos Git diferentes, documentando seu progresso. Ao final, você terá um histórico completo de desenvolvimento dividido por commits claros.

## Pré-requisitos

- Git instalado na sua máquina.
- Familiaridade com terminal.
- Editor de texto instalado (VS Code, Notepad++, nano etc.).
- Conta no GitHub (opcional para push remoto).

---

## Descrição da Atividade

Você irá criar um projeto simples chamado `meu-projeto`. Este projeto será desenvolvido em camadas, onde cada etapa representa uma modificação no conteúdo.

Você deverá:

- Inicializar um repositório Git.
- Criar e alternar entre branches.
- Fazer commits separados para cada etapa.
- Resolver conflitos locais.
- Visualizar e interpretar o histórico.
- (Opcional) Trabalhar com um repositório remoto.

---

## Passo a Passo

### 1. Crie a pasta do projeto e inicialize o Git

```bash
mkdir meu-projeto
cd meu-projeto
git init
```

---

### 2. Crie o arquivo principal do projeto

Crie um arquivo chamado `projeto.txt` e adicione uma estrutura inicial:

```
# Projeto Pessoal
Este é o início do meu projeto.
```

Salve e adicione ao Git:

```bash
git add projeto.txt
git commit -m "Cria arquivo principal com estrutura inicial"
```

---

### 3. Crie uma branch para a introdução

```bash
git checkout -b introducao
```

Adicione um novo parágrafo no `projeto.txt`:

```
## Introdução
Este projeto tem como objetivo demonstrar o uso avançado do Git.
```

```bash
git add projeto.txt
git commit -m "Adiciona seção de introdução"
```

---

### 4. Volte para a branch principal e crie outra branch para funcionalidades

```bash
git checkout main
git checkout -b funcionalidades
```

Adicione outra seção ao arquivo:

```
## Funcionalidades
- Uso de Git
- Branches e merges
- Histórico e conflitos
```

```bash
git add projeto.txt
git commit -m "Adiciona seção de funcionalidades"
```

---

### 5. Simule um conflito

Volte para a branch `main`, modifique a mesma seção da introdução com um texto diferente e faça commit:

```bash
git checkout main
```

Edite `projeto.txt`:

```
## Introdução
Texto alterado diretamente na main para causar conflito.
```

```bash
git add projeto.txt
git commit -m "Altera seção de introdução na main"
```

---

### 6. Tente fazer merge da branch `introducao` na `main`

```bash
git merge introducao
```

O Git irá identificar um **conflito**.

Abra o arquivo `projeto.txt`, você verá algo como:

```
<<<<<<< HEAD
Texto da main
=======
Texto da branch introducao
>>>>>>> introducao
```

Edite o texto para manter a versão desejada (ou combinar as duas), remova os símbolos `<<<<<<<`, `=======`, `>>>>>>>`, salve e depois:

```bash
git add projeto.txt
git commit -m "Resolve conflito entre main e introducao"
```

---

### 7. Faça o merge da branch funcionalidades

```bash
git merge funcionalidades
```

---

### 8. Visualize o histórico completo

```bash
git log --oneline --graph --all
```

Analise como os commits se relacionam visualmente.

---

### 9. (Opcional) Crie um repositório remoto no GitHub e envie seu projeto

No GitHub:
- Crie um novo repositório vazio.
- NÃO marque para criar README.

No terminal:

```bash
git remote add origin https://github.com/seu-usuario/meu-projeto.git
git branch -M main
git push -u origin main
```

---

## Comandos utilizados nesta atividade

- `git init`
- `git add`
- `git commit`
- `git checkout -b`
- `git merge`
- `git log --oneline --graph --all`
- `git remote add` (opcional)
- `git push` (opcional)

---

## Entregáveis

- O arquivo `projeto.txt` com todas as seções.
- O histórico de commits deve refletir as etapas da atividade.
- (Se remoto) Link do repositório no GitHub.

---

## Dúvidas

Se houver erros durante o merge ou push, leia com atenção as mensagens do Git, elas costumam indicar claramente o que precisa ser feito.

