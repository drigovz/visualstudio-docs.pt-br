---
title: Suporte ao controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156070"
---
# <a name="supporting-source-control"></a>Suporte para controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dá suporte a check-outs de arquivo, check-ins e outras operações de controle do código-fonte para seu projeto ou editor. Como um cliente de controle do código-fonte, o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] é projetado para interagir com um pacote de controle do código-fonte, como [!INCLUDE[vsvss](../../includes/vsvss-md.md)] o, que fornece arquivamento, controle de versão e instalações para um conjunto de arquivos definido dinamicamente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelo de pacotes de controle do código-fonte](../../extensibility/internals/model-for-source-control-packages.md)  
 Descreve as interfaces que um tipo de projeto deve implementar para dar suporte ao controle do código-fonte.  
  
 [Decisões de design](../../extensibility/internals/source-control-design-decisions.md)  
 Fornece perguntas cujas respostas mudam como você implementa um tipo de projeto.  
  
 [Detalhes da configuração](../../extensibility/internals/source-control-configuration-details.md)  
 Descreve como o controle do código-fonte de suporte altera a implementação de um tipo de projeto.  
  
 [Diretrizes adicionais para projetos e editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Discute as práticas recomendadas para editores e tipos de projeto.  
  
 [Detalhes de runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Descreve como registrar um projeto quando um usuário o adiciona a um sistema de controle de origem.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica ao ambiente ou ao pacote de controle do código-fonte que um arquivo está prestes a ser alterado na memória ou salvo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite que projetos e hierarquias se registrem com o controle do código-fonte e obtenham informações sobre o status do controle do código-fonte.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementado em um sistema de projeto para fornecer controle do código-fonte para arquivos de projeto e itens de projeto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Usado por projetos para consultar o ambiente para obter permissão para adicionar, remover ou renomear um arquivo ou diretório em uma solução.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica os clientes sobre as alterações feitas nos arquivos ou diretórios do projeto.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Fornece uma visão geral dos projetos como os blocos de construção básicos do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado). São fornecidos links para tópicos adicionais que explicam como os projetos controlam a criação e a compilação de código.
