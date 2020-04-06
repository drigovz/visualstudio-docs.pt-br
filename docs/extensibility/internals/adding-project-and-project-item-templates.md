---
title: Adicionando modelos de itens de projeto e projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710203"
---
# <a name="add-project-and-project-item-templates"></a>Adicionar modelos de itens de projeto e projeto
Ao criar seus próprios tipos de projeto, você deve fornecer suporte para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adicionar novos projetos e itens de projeto usando as caixas de diálogo padrão do ambiente de desenvolvimento integrado (IDE). Os tópicos a seguir discutem diferentes técnicas para aadição de projetos e itens do projeto.

## <a name="in-this-section"></a>Nesta seção
- [Contexto do projeto](../../extensibility/internals/project-context.md)

 Explica que o projeto fornece a maior parte das informações de contexto para o que acontece no ambiente.

- [Prioridade do projeto](../../extensibility/internals/project-priority.md)

 Explica que um item do projeto geralmente é membro de um projeto para ajudar a evitar a ambiguidade sobre qual projeto é usado para abrir o item.

- [Projeto arquivos diversos](../../extensibility/internals/miscellaneous-files-project.md)

 Fornece informações sobre os dois tipos de editores que podem ser usados para abrir arquivos em um projeto e o papel que o projeto desempenha na determinação de qual editor usar quando um item do projeto é aberto.

- [Registre modelos de projetos e itens](../../extensibility/internals/registering-project-and-item-templates.md)

 Explica o que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ocorre quando um projeto é criado.

- [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Explica o processo de adição de itens à caixa de diálogo **Adicionar novo item.**

- [Adicionar diretórios à caixa de diálogo do Novo Projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Fornece um exemplo de registro de um novo diretório que contém modelos personalizados disponibilizados por um VSPackage.

- [Adicionar diretórios à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Fornece um exemplo de registro de um novo conjunto de diretórios para a caixa de diálogo **Adicionar novo item.**

- [Comandos definidos pelo IDE para a ampliação de sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Lista diferentes tipos de itens de comando usados para estender sistemas de projeto.

- [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Lista CATIDs para objetos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]que [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]são [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usados para estender , e sistemas de projeto.

## <a name="related-sections"></a>Seções relacionadas
- [Como: Abrir editores específicos de projetos](../../extensibility/how-to-open-project-specific-editors.md)

 Fornece instruções passo-a-passo para abrir um item intrinsecamente vinculado a um editor específico para um projeto.

- [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)

 Fornece instruções passo-a-passo para abrir um editor padrão.

- [Subtipos do projeto](../../extensibility/internals/project-subtypes.md)

 Fornece links para tópicos conceituais do subtipo do projeto. Os subtipos do [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeto ampliam os projetos existentes.

- [Tipos de projetos](../../extensibility/internals/project-types.md)

 Fornece links para tópicos adicionais que oferecem informações sobre como projetar novos tipos de projetos.
