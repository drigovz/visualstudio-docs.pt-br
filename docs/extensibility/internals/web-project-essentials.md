---
title: Projeto Web Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703545"
---
# <a name="web-project-essentials"></a>Conceitos básicos do projeto Web
Projetos web criam aplicativos web. Você pode usar um projeto web para criar um aplicativo da Web que tenha páginas da Web inteligentes. Uma página da Web inteligente tem código do lado do servidor que torna a página da Web sob demanda.

 Usando linguagens de programação [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]tradicionais, como ou , você pode criar páginas da Web inteligentes para coletar e processar informações de um usuário, armazená-los em um banco de dados, e assim por diante.

- O modelo de código por trás associa arquivos de código-fonte dependentes com páginas da Web que têm a extensão de arquivo .aspx ou .asmx. Por exemplo, hello.aspx pode ter o arquivo de código-fonte dependente hello.aspx.cs.

- O código do lado do servidor associado a uma página da Web inteligente é compilado em um arquivo executável que está localizado na pasta web site /bin.

- Arquivos adicionais de código-fonte, como classes auxiliares que não estão associadas a uma página da Web específica, estão localizados na pasta Web site /App_Code.

  - Um projeto de site (WSP) gera um arquivo executável para cada página da Web inteligente. Arquivos executáveis adicionais são gerados a partir de quaisquer arquivos de código-fonte na pasta /App_Code.

  - Um projeto de aplicação web (WAP) produz um único arquivo executável que combina o código para todas as páginas da Web inteligentes, bem como todos os arquivos de origem na pasta /App_Code.

- O arquivo de solução para um projeto Web está localizado separadamente do próprio site da Web. Por padrão, os arquivos de solução estão\\localizados em \Documentos e Configurações\\*SuaConta*\Meus Documentos\\*\<Visual Studio ####>* \Projetos*SeuWebSite*.

  > [!NOTE]
  > Se você quiser manter o arquivo de solução com o site, basta movê-lo para lá e reabri-lo.

- Se você abrir um site que não tem nenhum arquivo de solução no Visual Studio, um novo arquivo de solução será gerado automaticamente para ele.

- Projetos web não têm arquivos de projeto. As informações do projeto são armazenadas no arquivo de solução, no arquivo web.config e em outros lugares.

- Adicionar propriedades globais a um projeto Web cria automaticamente um arquivo de armazenamento na pasta de solução de projeto Web.

- Uma página da Web inteligente pode ser associada a uma linguagem \<de programação do lado do servidor usando a diretiva Página ou a tag de script runat="servidor">.

- Além disso, as páginas da Web podem ter qualquer número de blocos de script do lado do cliente escritos em qualquer idioma de script.

- Um sistema de projeto de site é implementado adicionando [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] modelos de projeto e itens e registro ao projeto.

- Um sistema WAP é implementado como um subtipo de projeto, também chamado de sabor de projeto. O [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeto é aromatizado pelo subtipo WAP para criar o sistema WAP. Para obter mais informações sobre os subtipos do projeto, consulte [Subtipos do Projeto](../../extensibility/internals/project-subtypes.md).

- Uma página da Web inteligente combina HTML com uma linguagem de programação do lado do servidor. A linguagem do lado do servidor é chamada de linguagem contida. Para suportar uma linguagem contida, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> sistema de projetos web deve implementar a família de interfaces.

  - Para suportar o idioma contido em um editor, o serviço de linguagem HTML deve adiar a exibição de código de idioma contido para um serviço de idioma contido.

  - Os marcadores de erro (rabiscos vermelhos) devem ser sempre criados no buffer principal do editor de código.

## <a name="see-also"></a>Confira também
- [Projetos Web](../../extensibility/internals/web-projects.md)
