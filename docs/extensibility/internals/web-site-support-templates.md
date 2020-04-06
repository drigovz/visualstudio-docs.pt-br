---
title: Modelos de suporte ao site | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703461"
---
# <a name="web-site-support-templates"></a>Modelos de suporte a site
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Os modelos de projetos e itens do site da Web fornecem projetos e stubs de itens reutilizáveis e personalizáveis que aceleram o processo de desenvolvimento, removendo a necessidade de criar novos projetos e itens do site do zero. Para obter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mais informações sobre modelos, consulte [Criando modelos de projeto e itens](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Pasta de modelo de projeto
 Os modelos de projeto da Web são normalmente instalados em [ Visual Studio\\Installation*Path*]\Common7\IDE\ProjectTemplates\Web , cada um em uma subpasta que tem o nome da linguagem de programação da Web.

## <a name="project-file"></a>Arquivo de Projeto
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) requer uma extensão de arquivo de projeto como forma de mapear um modelo para o tipo de projeto correto. Como os projetos da Web não possuem um arquivo de projeto, a extensão de arquivo de projeto dummy .webproj está registrada para mapear o modelo para o tipo de projeto.

 Opcionalmente, uma seqüência de nomes de idioma pode ser adicionada ao modelo, para permitir que o sistema de projeto da Web defina o padrão de idioma na caixa de diálogo **Adicionar novo item** para itens com base no modelo. A seqüência deve ser a primeira linha do arquivo. Ele deve corresponder tanto ao nome registrado em AddItemLanguageName no registro do mecanismo IntelliSense, quanto ao nome registrado no Subtipo do Projeto (VsTemplate). Para obter mais informações, consulte [Atributos de suporte do site.](../../extensibility/internals/web-site-support-attributes.md)

 Se a seqüência não estiver presente, o sistema de projeto da Web tentará determinar o idioma padrão com base no atributo Language e nas extensões de arquivo das páginas adicionadas ao projeto Web pelo Modelo de Projeto.

## <a name="project-templates"></a>Modelos de projeto
 Os modelos de projeto do site da Web são usados para criar novos sites em resposta ao comando **Novo Site** no menu **Arquivo.** Três tipos de projetos de sites da Web são suportados atualmente:

- Projetos de sites vazios

- Projetos de sites

- Projetos de serviços web

### <a name="empty-web-site-projects"></a>Projetos de sites vazios
 Esses arquivos criam um novo site vazio em resposta ao comando **Empty Web Site,** que está disponível após a escolha **do site File** > **New :**

- EmptyWeb.vstemplate

     O arquivo de modelo que orienta a criação do novo site vazio.

- EmptyWeb.webproj

     Este arquivo é um artefato do sistema de modelo de projeto. Ele satisfaz a referência do arquivo de projeto no arquivo EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Projetos de sites
 Esses arquivos criam um novo site em resposta ao comando **ASP.NET Web Site,** que está disponível após a escolha **do Site do Arquivo** > **Novo**:

- Default.aspx

     A página inicial padrão do novo site. O atributo Language especifica o código atrás da linguagem, e o atributo CodeFile especifica o arquivo dependente que contém o código por trás associado a esta página.

- Default.aspx. *extensão*

     O arquivo dependente que contém o código por trás do código para a página inicial padrão. O código por trás da linguagem determina a *extensão* deste arquivo.

- web.config

     O arquivo raiz de configuração do site.site.

- WebApplication.vstemplate

     O arquivo de modelo que determina o conteúdo da solução do site da Web e força a criação da pasta App_Data.

- WebApplication.webproj

     Este arquivo é um artefato do sistema de modelo de projeto. Ele satisfaz a referência do arquivo do projeto no arquivo WebApplication.vstemplate.

### <a name="web-service-projects"></a>Projetos de Serviços Web
 Esses arquivos criam um novo site em resposta ao comando **ASP.NET Web Service,** que está disponível após a escolha **do site File** > **New:**

- Service.asmx

     A página HTML para o novo serviço Web. O atributo Language especifica o código atrás da linguagem, e o atributo CodeBehind especifica o arquivo dependente que contém o código por trás associado a este serviço.

- Serviço. *Extensão*

     O arquivo dependente que implementa a classe de serviço. O código por trás da linguagem determina a *extensão* deste arquivo.

- web.config

- O arquivo raiz de configuração do site.site.

- WebService.vstemplate

     O arquivo de modelo que determina o conteúdo da solução do site e força a criação das pastas App_Data e App_Code. O serviço. o arquivo *de extensão* é copiado para a pasta App_Code.

- WebService.webproj

     Este arquivo é um artefato do sistema de modelo de projeto. Ele satisfaz a referência do arquivo de projeto no arquivo WebService.vstemplate.

## <a name="project-item-template-folder"></a>Pasta de modelo de item do projeto
 Os modelos de itens de projeto da Web são normalmente instalados em [ Visual Studio\\Installation*Path*]\Common7\IDE\ItemTemplates\Web , cada um em uma subpasta que tem o nome de sua linguagem de programação web.

## <a name="project-item-templates"></a>Modelos de itens do projeto
 Os modelos de itens do projeto do site da Web são usados para adicionar novas páginas da Web a um site da Web em resposta ao comando **Adicionar item existente.** Esses tipos de páginas da Web são suportadas atualmente:

- Nova classe

- Nova página HTML

- Novo formulário da Web

- Nova página-mestre

### <a name="new-class"></a>Nova Classe
 Este modelo cria um novo arquivo de origem que define uma classe vazia em resposta ao **comando Adicionar nova classe.**

- Classe. *Extensão*

     O arquivo de origem que implementa a classe vazia. O código por trás da linguagem determina a *extensão* deste arquivo.

- Class.vstemplate

     O arquivo de modelo que cria o arquivo de origem e determina seu conteúdo.

### <a name="new-html-page"></a>Nova página HTML
 Este modelo cria uma nova página da Web em resposta ao **comando Adicionar nova página HTML.**

- HTMLPage.htm

     O conteúdo inicial da página da Web. Esta página da Web normalmente não tem código associado atrás de um arquivo dependente. Para criar uma página inteligente com um arquivo de código associado atrás, use o modelo Formulário da Web em vez disso.

- HTMLPage.vstemplate

     O arquivo de modelo que cria a página da Web e determina seu conteúdo.

### <a name="new-webform"></a>Nova WebForm
 Este modelo cria uma nova página da Web inteligente em resposta ao **comando Adicionar novo formulário da Web.**

 Para criar um código dependenteatrás do arquivo-fonte, selecione **Colocar código em arquivo separado**. Caso contrário, uma única página da Web é criada \<que tem um bloco de scripts vazio e nenhuma diretiva % página %> para conectar um arquivo dependente.

 Para criar uma página de conteúdo para uma página-mestre selecionada, **selecione Selecionar página-mestre**.

- WebForm.aspx

     O conteúdo inicial da página da Web. Esta página da Web não tem código associado atrás de um arquivo dependente.

- WebForm_cb.aspx

     O conteúdo inicial da página da Web. Esta página da Web tem um código associado atrás de um arquivo dependente.

- Codebehind. *Extensão*

     O arquivo dependente que implementa a classe webform. O código por trás da linguagem determina a *extensão* deste arquivo.

- ContentPage.aspx

     O conteúdo inicial da página da Web como uma página de conteúdo. Esta página da Web não tem código associado atrás de um arquivo dependente.

- ContentPage_cb.aspx

     O conteúdo inicial da página da Web como uma página de conteúdo. Esta página da Web tem um código associado atrás de um arquivo dependente.

- WebForm.vstemplate

     O arquivo de modelo que determina o conteúdo da nova página da Web e seu arquivo dependente, se houver.

### <a name="new-master-page"></a>Nova página-mestre
 Este modelo cria uma nova página-mestre em resposta ao **comando Adicionar nova página-mestre.**

 Para criar um código dependenteatrás do arquivo-fonte, selecione **Colocar código em arquivo separado**. Caso contrário, uma única página da Web é criada \<que tenha um bloco de scripts vazio e nenhuma diretiva % página %> para conectar um arquivo dependente.

- MasterPage.master

     O conteúdo inicial da página principal. Esta página-mestre não tem código associado atrás de arquivo dependente.

- MasterPage_cb.mestre

     O conteúdo inicial da página principal. Esta página-mestre tem um código associado atrás de um arquivo dependente.

- Codebehind. *extensão*

     O arquivo dependente que implementa a classe de página mestre. O código por trás da linguagem determina a *extensão* deste arquivo.

- MasterPage.vstemplate

     O arquivo de modelo que determina o conteúdo da nova página-mestre e seu arquivo dependente, se houver.

## <a name="see-also"></a>Confira também
- [Suporte a site](../../extensibility/internals/web-site-support.md)
