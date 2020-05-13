---
title: Suporte ao Controle de Fontes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704725"
---
# <a name="supporting-source-control"></a>Suporte para controle do código-fonte
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]suporta check-outs de arquivos, check-ins e outras operações de controle de origem para seu projeto ou editor. Como cliente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controle de origem, foi projetado para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]interagir com um pacote de controle de origem, como, como, que fornece instalações de arquivamento, versão e controle para um conjunto de arquivos dinamicamente definidos.

## <a name="in-this-section"></a>Nesta seção
- [Modelo de pacotes de controle do código-fonte](../../extensibility/internals/model-for-source-control-packages.md)

 Descreve as interfaces que um tipo de projeto deve implementar para suportar o controle de origem.

- [Decisões de design](../../extensibility/internals/source-control-design-decisions.md)

 Fornece perguntas cujas respostas mudam a forma como você implementa um tipo de projeto.

- [Detalhes de configuração](../../extensibility/internals/source-control-configuration-details.md)

 Descreve como o controle de origem de suporte altera a implementação de um tipo de projeto.

- [Diretrizes adicionais para projetos e editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Discute as melhores práticas para tipos de projetos e editores.

- [Detalhes de runtime](../../extensibility/internals/source-control-runtime-details.md)

 Descreve como registrar um projeto quando um usuário o adiciona a um sistema de controle de origem.

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Indica para o ambiente ou pacote de controle de origem que um arquivo está prestes a ser alterado na memória ou salvo.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Permite que projetos e hierarquias se registrem com o controle de origem e obtenham informações sobre o status de controle de origem.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Implementado em um sistema de projeto para fornecer controle de origem para arquivos de projeto e itens de projeto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Usado por projetos para consultar o ambiente para obter permissão para adicionar, remover ou renomear um arquivo ou diretório em uma solução.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Notifica clientes de alterações que foram feitas em arquivos de projeto ou diretórios.

## <a name="related-sections"></a>Seções relacionadas
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece uma visão geral dos projetos como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os blocos básicos de construção do ambiente de desenvolvimento integrado (IDE). Links são fornecidos para tópicos adicionais que explicam como os projetos controlam a construção e compilação de códigos.
