---
title: Adicionando projetos e modelos de item de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203863"
---
# <a name="adding-project-and-project-item-templates"></a>Adicionando o projeto e os modelos de item do projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ao criar seus próprios tipos de projeto, você deve fornecer suporte para adicionar novos projetos e itens de projeto usando as caixas de diálogo padrão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE). Os tópicos a seguir discutem técnicas diferentes para adicionar projetos e itens de projeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Contexto do projeto](../../extensibility/internals/project-context.md)  
 Explica que o projeto fornece a maioria das informações de contexto para o que ocorre no ambiente.  
  
 [Prioridade do projeto](../../extensibility/internals/project-priority.md)  
 Explica que um item de projeto é geralmente um membro de um projeto para ajudar a evitar ambigüidade sobre qual projeto é usado para abrir o item.  
  
 [Projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)  
 Fornece informações sobre os dois tipos de editores que podem ser usados para abrir arquivos em um projeto e a função que o projeto desempenha para determinar qual editor deve ser usado quando um item de projeto é aberto.  
  
 [Registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)  
 Explica o que ocorre quando um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto é criado.  
  
 [Adicionando itens às caixas de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Explica o processo para adicionar itens à caixa de diálogo **Adicionar novo item** .  
  
 [Adicionar diretórios à caixa de diálogo Novo Projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Fornece um exemplo de registro de um novo diretório que contém modelos personalizados disponibilizados por um VSPackage.  
  
 [Adicionando diretórios à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Fornece um exemplo de registro de um novo conjunto de diretórios para a caixa de diálogo **Adicionar novo item** .  
  
 [Comandos definidos pelo IDE para estender sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Lista diferentes tipos de itens de comando usados para estender sistemas de projeto.  
  
 [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Lista os CATIDs para objetos que são usados para estender [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] , [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] sistemas de projeto.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)  
 Fornece instruções passo a passo para abrir um item associado intrinsecamente a um editor específico para um projeto.  
  
 [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)  
 Fornece instruções passo a passo para abrir um editor padrão.  
  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Fornece links para tópicos conceituais de subtipo de projeto. Os subtipos de projeto estendem [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projetos e existentes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos adicionais que oferecem informações sobre como criar novos tipos de projeto.
