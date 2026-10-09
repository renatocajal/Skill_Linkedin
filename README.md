# Skill de Consultor de LinkedIn para Claude Code

Uma skill para o Claude Code que faz o papel de um recrutador e estrategista de posicionamento: diagnostica seu perfil do LinkedIn, reescreve headline e Sobre, adapta o perfil a uma vaga e escreve posts com as palavras-chave que o seu público busca.

Tudo roda no seu computador, com o Claude Code. A skill não acessa sua conta do LinkedIn; você cola o texto do perfil ou envia o PDF.

---

## O que a skill faz

1. **Diagnóstico do perfil**: nota de 0 a 100 por bloco, falhas críticas, palavras-chave presentes e ausentes, plano de ações com textos prontos.
2. **Reescrita de headline e Sobre**: versões para clientes e para recrutadores.
3. **Adaptação a vaga ou projeto**: análise de fit, palavras-chave da vaga e carta curta.
4. **Posts**: ganchos, variações e hashtags.
5. **Foto e banner**: prompts para gerar a imagem e textos para o banner.

---

## Requisitos

- [Claude Code](https://claude.com/claude-code) instalado (terminal, app desktop ou extensão do VS Code).
- Uma conta Claude com acesso ao Claude Code.
- Um perfil do LinkedIn para analisar (você pode criar a conta gratuita se ainda não tiver).

---

## Instalação

### Passo 1: baixe a skill

Opção A, pelo GitHub: clique em **Code > Download ZIP**, descompacte o arquivo.

Opção B, com git:

```bash
git clone https://github.com/SEU-USUARIO/linkedin-consultor-skill.git
```

> Troque `SEU-USUARIO` pelo endereço real do repositório.

### Passo 2: copie a pasta para a pasta de skills do Claude

A pasta precisa ficar em `~/.claude/skills/` com o nome `linkedin-consultor`.

**Windows (PowerShell):**

```powershell
Copy-Item -Recurse ".\linkedin-consultor-skill" "$env:USERPROFILE\.claude\skills\linkedin-consultor"
```

**macOS / Linux:**

```bash
mkdir -p ~/.claude/skills
cp -r linkedin-consultor-skill ~/.claude/skills/linkedin-consultor
```

Confira se o arquivo ficou no lugar certo: `~/.claude/skills/linkedin-consultor/SKILL.md` deve existir.

### Passo 3: configure o seu posicionamento

Dentro da pasta da skill, copie o arquivo de exemplo e preencha com as suas informações:

**Windows:**

```powershell
Copy-Item "$env:USERPROFILE\.claude\skills\linkedin-consultor\meu-posicionamento.exemplo.md" "$env:USERPROFILE\.claude\skills\linkedin-consultor\meu-posicionamento.md"
```

**macOS / Linux:**

```bash
cp ~/.claude/skills/linkedin-consultor/meu-posicionamento.exemplo.md ~/.claude/skills/linkedin-consultor/meu-posicionamento.md
```

Abra `meu-posicionamento.md` e preencha: quem você é, o que faz, para quem, resultados reais e palavras-chave. Quanto mais preciso, melhor o diagnóstico.

> Não preencha o que não é verdade. A skill foi feita para não inventar números, e um resultado falso no perfil pode custar caro numa entrevista ou numa proposta.

---

## Como usar

Abra o Claude Code na pasta que quiser (ele pode ser usado em qualquer diretório) e converse com ele em português.

### Analisar o perfil (diagnóstico)

Esse é o uso principal. Você tem duas formas de enviar o perfil:

**Opção 1: colar o texto**

1. Abra o seu perfil no LinkedIn.
2. Copie a headline, o Sobre e as experiências.
3. Cole no chat com um pedido, por exemplo:

   > Faça o diagnóstico do meu perfil do LinkedIn. Meu objetivo é captar clientes.
   >
   > [cole aqui o texto do perfil]

**Opção 2: enviar o PDF**

1. No LinkedIn, abra o seu perfil e clique em **Mais > Salvar como PDF**.
2. Salve o arquivo na sua pasta, por exemplo `perfil-meu-nome.pdf`.
3. No Claude Code, peça:

   > Faça o diagnóstico do meu perfil. O arquivo está em perfil-meu-nome.pdf.

A skill vai responder com:

- nota geral e nota por bloco;
- o que está bom e as falhas mais graves, em ordem de impacto;
- palavras-chave presentes e ausentes;
- um plano de ações com textos prontos para colar.

O diagnóstico é salvo como `diagnostico-AAAA-MM-DD.md`, na pasta da skill, se você pedir. Ele fica no seu computador e está no `.gitignore`.

### Comparar antes e depois

Depois de fazer as mudanças no perfil, peça uma nova rodada:

> Refaça o diagnóstico do meu perfil e compare com o diagnóstico anterior.

Os diagnósticos são comparados lado a lado para você ver o que melhorou.

### Outros usos

- **Reescrever headline e Sobre:** "Reescreva minha headline e meu Sobre, em duas versões: uma para clientes e outra para recrutadores."
- **Adaptar a uma vaga:** cole a descrição da vaga e peça "Avalie o fit com essa vaga e ajuste meu Sobre."
- **Escrever um post:** "Escreva um post sobre [assunto], em três variações: curta, técnica e de história pessoal."
- **Gerar foto ou banner:** "Crie um prompt em inglês para gerar uma foto profissional para o meu LinkedIn."

---

## Estrutura da pasta

```
linkedin-consultor-skill/
├── SKILL.md                       # instruções da skill (não precisa editar)
├── meu-posicionamento.exemplo.md  # modelo para você preencher
├── .gitignore                     # evita subir seus dados pessoais
├── LICENSE                        # licença MIT
└── README.md                      # este arquivo
```

Depois que você configurar, a pasta `~/.claude/skills/linkedin-consultor/` também terá `meu-posicionamento.md` e os diagnósticos gerados. Esses arquivos são seus e não devem ir para o GitHub.

---

## Privacidade

- O perfil e o posicionamento ficam no seu computador e são enviados ao Claude apenas durante a conversa, como qualquer texto que você cola no chat.
- Não coloque senhas, dados bancários ou documentos pessoais no perfil ou no `meu-posicionamento.md`.
- Não suba `meu-posicionamento.md` nem os diagnósticos para repositórios públicos. O `.gitignore` já ajuda com isso.

---

## Solução de problemas

**O Claude Code não reconhece a skill.**
Confira se o arquivo está em `~/.claude/skills/linkedin-consultor/SKILL.md` e reinicie o Claude Code.

**A skill pergunta tudo de novo.**
Verifique se você criou `meu-posicionamento.md` (sem o `.exemplo`) dentro da pasta da skill.

**O PDF não é lido.**
Tente colar o texto diretamente no chat, ou gere o PDF de novo pelo botão **Salvar como PDF** do perfil.

---

## Licença

Distribuído sob a [licença MIT](LICENSE). Você pode usar, copiar, modificar e redistribuir, inclusive para fins comerciais, desde que mantenha o aviso de copyright e a licença.
