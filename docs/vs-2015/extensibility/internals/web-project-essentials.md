---
title: Conceitos básicos do projeto Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825623"
---
# <a name="web-project-essentials"></a>Conceitos básicos do projeto Web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projetos da Web criam aplicativos Web. Você pode usar um projeto Web para criar um aplicativo Web que tenha páginas da Web inteligentes. Uma página da Web inteligente tem um código do lado do servidor que renderiza a página da Web sob demanda.  
  
 Usando linguagens de programação tradicionais, como [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../includes/csprcs-md.md)] , você pode criar páginas da Web inteligentes para coletar e processar informações de um usuário, armazená-las em um banco de dados e assim por diante.  
  
- O modelo code-behind associa arquivos de código-fonte dependentes com páginas da Web que têm a extensão de arquivo. aspx ou. asmx. Por exemplo, Hello. aspx pode ter o arquivo de código-fonte dependente hello.aspx.cs.  
  
- O código do lado do servidor associado a uma página da Web inteligente é compilado em um arquivo executável localizado na pasta/bin do site da Web.  
  
- Arquivos de código-fonte adicionais, como as classes auxiliares que não estão associadas a uma página da Web específica, estão localizados na pasta site/App_Code.  
  
  - Um WSP (projeto de site da Web) gera um arquivo executável para cada página da Web inteligente. Arquivos executáveis adicionais são gerados de qualquer arquivo de código-fonte na pasta/App_Code.  

  - Um WAP (projeto de aplicativo Web) produz um único arquivo executável que combina o código para todas as páginas da Web inteligentes, bem como todos os arquivos de origem na pasta/App_Code.  
  
- O arquivo de solução para um projeto Web está localizado separadamente do site da Web. Por padrão, os arquivos de solução estão localizados em \Documents and Settings \\ *suaconta*\Meus documentos \\ *\<Visual Studio ####>* \projects \\ *YourWebSite*.  
  
    > [!NOTE]
    > Se você quiser manter o arquivo da solução com o site, basta movê-lo e reabri-lo.  
  
- Se você abrir um site que não tem nenhum arquivo de solução no Visual Studio, um novo arquivo de solução será gerado automaticamente para ele.  
  
- Projetos da Web não têm arquivos de projeto. As informações do projeto são armazenadas no arquivo da solução, no arquivo de web.config e em outro lugar.  
  
- A adição de propriedades globais a um projeto Web cria automaticamente um arquivo de armazenamento na pasta de solução do projeto Web.  
  
- Uma página da Web inteligente pode ser associada a uma linguagem de programação do lado do servidor usando a diretiva Page ou a \<script runat="server"> marca.  
  
- Além disso, as páginas da Web podem ter qualquer número de blocos de script do lado do cliente escritos em qualquer linguagem de script.  
  
- Um sistema de projeto de site é implementado adicionando modelos de projeto e item e registro ao [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] projeto.  
  
- Um sistema WAP é implementado como um subtipo de projeto, também chamado de tipo de projeto. O [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] projeto é recriado pelo subtipo WAP para criar o sistema WAP. Para obter mais informações sobre subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
- Uma página da Web inteligente combina HTML com uma linguagem de programação no servidor. O idioma do lado do servidor é chamado de idioma contido. Para dar suporte a um idioma contido, o sistema de projeto da Web deve implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> família de interfaces.  
  
  - Para dar suporte ao idioma contido em um editor, o serviço de linguagem HTML deve adiar a exibição do código de idioma contido em um serviço de linguagem independente.  

  - Marcadores de erro (ondulados vermelho) sempre devem ser criados no buffer primário do editor de código.  
  
## <a name="see-also"></a>Consulte Também  
 [Projetos Web](../../extensibility/internals/web-projects.md)
