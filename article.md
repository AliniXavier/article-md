# article-md
# article-md
# Azure Open AI em VNet - DEV Community

Kenichiro Nakamura  
Postado em 12 de outubro de 2023  

## Azure Open AI em VNet

GPT modelos estão hospedados em vários fornecedores de serviço no momento, e o Microsoft Azure é um deles.  
Embora os modelos em si sejam os mesmos, existem muitas diferenças, incluindo:  
- custo  
- funcionalidades  
- tipos de modelos e versões  
- localização geográfica  
- segurança  
- suporte  
- etc.  

Um dos aspectos mais importantes ao usá-lo em um ambiente corporativo é, claro, a segurança.  
Ao usar os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI de e dentro da VNet, portanto, nenhuma informação está fluindo publicamente.

### Implantação de Exemplo

O repositório de amostras do Azure fornece arquivos bicep de exemplo para implantar o Azure Open AI em um ambiente VNet.  
GitHub: [openai-enterprise-iac](https://github.com/Azure-Samples/openai-enterprise-iac)

As principais características que o bicep utiliza são:  
- VNet  
- Integração de VNet para Web App  
- Endpoint Privado para Azure Open AI  
- Endpoint Privado para Pesquisa Cognitiva  
- Zona DNS Privada  

Usando esses recursos, todo o tráfego de saída do Web App é roteado apenas dentro da VNet e todos os nomes são resolvidos em endereços IP privados. O Open AI e a Pesquisa Cognitiva encerram o endereço IP público, portanto, não há mais um endpoint de interface pública disponível.

### Implantar

O arquivo bicep implantará os seguintes recursos do Azure.  
Vamos implantar e confirmar como funciona. Criei um grupo de recursos na região East US para meu próprio teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Assim que eu executar o comando acima, vejo que a implantação começou.  
Aguarde até que a implantação seja concluída.

### Teste

Vamos ver se a implantação foi bem-sucedida.  
#### Azure Open AI

Vamos tentar o acesso público primeiro.  
Consegui criar uma implantação sem nenhum problema. Mas quando tento pelo Chat playground no meu Portal do Azure, vejo o seguinte erro.  
E quanto ao acesso via API Web?  
De uma ferramenta avançada do App Service, faço login na sessão Bash e primeiro faço o ping na URL do serviço.  
Vejo que o endereço IP privado atribuído ao Endpoint Privado é retornado.  
Em seguida, uso o comando curl para enviar uma solicitação ao endpoint.

---

## Comentários Principais
(0)  
Assinar  
Pessoal  
Usuário Confiável  
Criar modelo  
Modelos permitem que você responda rapidamente a perguntas frequentes ou armazene trechos para reutilização.  
Enviar  
Pré-visualizar  
Desconsiderar  

## Código de Conduta

• Denunciar abuso  
Você tem certeza de que deseja ocultar este comentário? Ele ficará oculto em sua postagem, mas ainda será visível através do permalink do comentário.  
Ocultar comentários filhos também  
Confirmar  
Para ações adicionais, você pode considerar bloquear esta pessoa e/ou denunciar abuso.

Ler próximo  
- Duas maneiras de usar Pester para simular objetos com parâmetros fortemente tipados  
Mark Wragg - 24 de outubro  
- Linux no Termux  
jeff dennis - 21 de outubro  
- Descobrindo os Últimos Recursos do AWS CloudFront: Melhorando Desempenho e Segurança  
Fady Nabil - 23 de novembro  
- Erro InvalidContentLink em implantações ARM  
Frans - 20 de outubro  

### Kenichiro Nakamura

Seguir  
Entrou em 3 de fevereiro de 2018  

Mais de  
Kenichiro Nakamura  
- Azure ML Prompt flow: Use segurança de conteúdo antes de enviar uma solicitação ao LLM  
- Não perca tempo escrevendo README, use readme-ai em vez disso  
- C#: Azure Open AI e Chamada de Função  

Agradecimentos ao nosso Patrocinador Diamante  
Neon  
por apoiar nossa comunidade.  

---

DEV Community — Uma rede social construtiva e inclusiva para desenvolvedores de software. Com você a cada passo de sua jornada.  
Início  
DEV++  
Podcasts  
Vídeos  
Tags  
Ajuda DEV  
Loja Forem  
Anuncie no DEV  
Desafios DEV  
Destaque DEV  
Sobre  
Contato  
Banco de Dados Postgres Gratuito  
Guias  
Comparações de Software  
Código de Conduta  
Política de Privacidade  
Termos de Uso  

Construído em  
Forem — o software de código aberto que alimenta o DEV e outras comunidades inclusivas.  
Feito com amor e Ruby on Rails.  
DEV Community © 2016 - 2024.  
Somos um lugar onde codificadores compartilham, se mantêm atualizados e desenvolvem suas carreiras.  

Entrar  
Criar conta  
# Azure Open AI em VNet - DEV Community

Kenichiro Nakamura  
Postado em 12 de outubro de 2023  

## Azure Open AI em VNet

GPT modelos estão hospedados em vários fornecedores de serviço no momento, e o Microsoft Azure é um deles.  
Embora os modelos em si sejam os mesmos, existem muitas diferenças, incluindo:  
- custo  
- funcionalidades  
- tipos de modelos e versões  
- localização geográfica  
- segurança  
- suporte  
- etc.  

Um dos aspectos mais importantes ao usá-lo em um ambiente corporativo é, claro, a segurança.  
Ao usar os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI de e dentro da VNet, portanto, nenhuma informação está fluindo publicamente.

### Implantação de Exemplo

O repositório de amostras do Azure fornece arquivos bicep de exemplo para implantar o Azure Open AI em um ambiente VNet.  
GitHub: [openai-enterprise-iac](https://github.com/Azure-Samples/openai-enterprise-iac)

As principais características que o bicep utiliza são:  
- VNet  
- Integração de VNet para Web App  
- Endpoint Privado para Azure Open AI  
- Endpoint Privado para Pesquisa Cognitiva  
- Zona DNS Privada  

Usando esses recursos, todo o tráfego de saída do Web App é roteado apenas dentro da VNet e todos os nomes são resolvidos em endereços IP privados. O Open AI e a Pesquisa Cognitiva encerram o endereço IP público, portanto, não há mais um endpoint de interface pública disponível.

### Implantar

O arquivo bicep implantará os seguintes recursos do Azure.  
Vamos implantar e confirmar como funciona. Criei um grupo de recursos na região East US para meu próprio teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Assim que eu executar o comando acima, vejo que a implantação começou.  
Aguarde até que a implantação seja concluída.

### Teste

Vamos ver se a implantação foi bem-sucedida.  
#### Azure Open AI

Vamos tentar o acesso público primeiro.  
Consegui criar uma implantação sem nenhum problema. Mas quando tento pelo Chat playground no meu Portal do Azure, vejo o seguinte erro.  
E quanto ao acesso via API Web?  
De uma ferramenta avançada do App Service, faço login na sessão Bash e primeiro faço o ping na URL do serviço.  
Vejo que o endereço IP privado atribuído ao Endpoint Privado é retornado.  
Em seguida, uso o comando curl para enviar uma solicitação ao endpoint.

---

## Comentários Principais
(0)  
Assinar  
Pessoal  
Usuário Confiável  
Criar modelo  
Modelos permitem que você responda rapidamente a perguntas frequentes ou armazene trechos para reutilização.  
Enviar  
Pré-visualizar  
Desconsiderar  

## Código de Conduta

• Denunciar abuso  
Você tem certeza de que deseja ocultar este comentário? Ele ficará oculto em sua postagem, mas ainda será visível através do permalink do comentário.  
Ocultar comentários filhos também  
Confirmar  
Para ações adicionais, você pode considerar bloquear esta pessoa e/ou denunciar abuso.

Ler próximo  
- Duas maneiras de usar Pester para simular objetos com parâmetros fortemente tipados  
Mark Wragg - 24 de outubro  
- Linux no Termux  
jeff dennis - 21 de outubro  
- Descobrindo os Últimos Recursos do AWS CloudFront: Melhorando Desempenho e Segurança  
Fady Nabil - 23 de novembro  
- Erro InvalidContentLink em implantações ARM  
Frans - 20 de outubro  

### Kenichiro Nakamura

Seguir  
Entrou em 3 de fevereiro de 2018  

Mais de  
Kenichiro Nakamura  
- Azure ML Prompt flow: Use segurança de conteúdo antes de enviar uma solicitação ao LLM  
- Não perca tempo escrevendo README, use readme-ai em vez disso  
- C#: Azure Open AI e Chamada de Função  

Agradecimentos ao nosso Patrocinador Diamante  
Neon  
por apoiar nossa comunidade.  
