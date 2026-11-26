# Open Hands
 
Sistema web de gestão para ONGs. Várias organizações podem se cadastrar, e cada uma gerencia apenas os seus próprios assistidos, doações, entregas e voluntários, com controle de estoque e relatórios de prestação de contas.
 
**Demonstração:** `https://SEU-USUARIO.github.io/open-hands/` (troque pelo endereço do seu GitHub Pages)
 
> Projeto desenvolvido como Projeto de Extensão do curso de Ciência da Computação (Unopar/Anhanguera), no Programa de Contexto à Comunidade. O cenário é uma simulação: ONGs, nomes e números usados nos exemplos são fictícios.
 
## Funcionalidades
 
- **Várias ONGs no mesmo sistema**, cada uma protegida por senha própria.
- **Assistidos:** cadastro, edição, busca e exclusão, com aviso de possível duplicidade (mesmo documento, ou mesmo nome e telefone).
- **Doações e entregas:** registro por data, item e quantidade, com entregas vinculadas a um assistido.
- **Estoque por item:** saldo calculado automaticamente (doações menos entregas), com destaque em vermelho quando fica negativo.
- **Voluntários:** cadastro com função e disponibilidade.
- **Relatório por período:** indicadores de doações, entregas e famílias atendidas, com impressão.
- **Exportação em CSV** de cada lista e do relatório.
- **Backup em JSON:** exportar e importar uma ONG inteira, o que também permite levá-la a outro aparelho.
- **Interface em estilo Metro UI:** tiles planos e coloridos, responsiva, com tema claro e escuro conforme o aparelho.
## Tecnologias
 
- HTML, CSS e JavaScript puro, em um único arquivo `index.html`, sem dependências nem etapa de build.
- Armazenamento no `localStorage` do navegador.
- Web Crypto API (SHA-256) para o hash das senhas.
- Hospedagem estática no GitHub Pages.
## Como publicar no GitHub Pages
 
1. Crie um repositório (por exemplo, `open-hands`) e envie o `index.html`.
2. Em **Settings → Pages**, escolha a branch principal e a pasta raiz (`/root`).
3. Aguarde alguns minutos e acesse `https://seu-usuario.github.io/open-hands/`.
Para testar localmente, basta abrir o `index.html` no navegador.
 
## Como usar
 
1. Na tela inicial, clique em **Cadastrar ONG** e defina nome, cidade, responsável e uma senha de pelo menos 6 caracteres.
2. Entre na ONG pelo tile correspondente.
3. Cadastre assistidos, registre doações e entregas e acompanhe o estoque no painel.
4. Em **Relatório**, escolha o período para gerar os indicadores.
5. Em **Ajustes**, exporte o backup com frequência.
## Estrutura de dados
 
```text
ONG         { id, nome, cidade, resp, h (hash da senha),
              families[], donations[], deliveries[], volunteers[] }
Assistido   { id, nome, doc, tel, membros, end, obs }
Doação      { id, data, doador, item, qtd, obs }
Entrega     { id, data, fam (id do assistido), item, qtd }
Voluntário  { id, nome, tel, func, disp }
```
 
## Segurança e privacidade
 
- A senha é guardada apenas como hash SHA-256 com sal, nunca em texto puro.
- Todo texto digitado é escapado antes de ser exibido (prevenção de XSS).
- A exportação CSV neutraliza células que começam com `=`, `+`, `-` ou `@` (injeção de fórmulas).
- A importação de backup valida o formato e aproveita só os campos esperados.
**Limitações importantes**
 
- Os dados ficam **somente no navegador do aparelho**, e não são sincronizados entre aparelhos. Limpar os dados do navegador apaga tudo, por isso faça backups.
- A senha protege contra acesso casual, mas **não equivale à segurança de um servidor**, já que tudo está no próprio aparelho.
- Cadastre apenas os dados necessários e observe a LGPD (Lei nº 13.709/2018) se for usar com famílias reais.
## Próximos passos
 
- Banco de dados online (Firebase ou Supabase) com login por usuário e perfis de acesso.
- PWA, com funcionamento offline e instalação no celular.
- Relatório em PDF e gráficos no painel.
- Política de privacidade e termo de consentimento para os assistidos.
## Autor
 
**Bruno Nunes da Silva** - Ciência da Computação, Unopar/Anhanguera.
 
## Licença
 
Defina a licença do repositório (por exemplo, MIT) e adicione o arquivo `LICENSE`.
 
