---
title: Hierarquias no Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708183"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarquias no Visual Studio
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) exibe um projeto como *hierarquia.* No IDE, uma hierarquia é uma árvore de nódulos, onde cada nó tem um conjunto de propriedades associadas. Uma *hierarquia de projeto* é um contêiner que contém os itens do projeto, as relações dos itens e as propriedades e comandos associados dos itens.

 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você gerencia hierarquias de projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>usando a interface hierárquica, . A <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface redireciona os comandos que você invoca de itens de projeto para a janela de hierarquia apropriada em vez do manipulador de comando padrão.

## <a name="project-hierarchies"></a>Hierarquias de projetos
 Cada hierarquia de projeto contém itens que você pode visualizar e editar. Esses itens variam dependendo do tipo de projeto. Por exemplo, um projeto de banco de dados pode conter procedimentos armazenados, visualizações de banco de dados e tabelas de banco de dados. Um projeto de linguagem de programação, por outro lado, provavelmente incluirá arquivos de origem e arquivos de recursos para bitmaps e caixas de diálogo. Hierarquias podem ser aninhadas, o que lhe dá alguma flexibilidade adicional ao criar uma hierarquia de projeto.

 Quando você cria um novo tipo de projeto, o tipo de projeto controla o conjunto completo de itens que podem ser editados nele. No entanto, os projetos podem conter itens para os quais eles não têm suporte de edição. Por exemplo, os projetos Visual C++ podem conter arquivos HTML, mesmo que o Visual C++ não forneça nenhum editor personalizado para o tipo de arquivo HTML.

 Hierarquias gerenciam a persistência de itens que contêm. A implementação da hierarquia deve controlar quaisquer propriedades especiais que afetem a persistência dos itens dentro da hierarquia. Por exemplo, se os itens representam objetos em um repositório em vez de arquivos, a implementação da hierarquia deve controlar a persistência desses objetos. O próprio IDE direciona a hierarquia para salvar os itens em conformidade com a entrada do usuário, mas o IDE não controla nenhuma ação necessária para salvar esses itens. Em vez disso, o projeto está no controle.

 Quando um usuário abre um item em um editor, a hierarquia que controla esse item é selecionada e se torna a hierarquia ativa. A hierarquia selecionada determina o conjunto de comandos disponíveis para agir no item. O rastreamento do foco do usuário dessa forma permite que a hierarquia reflita o contexto atual do usuário.

## <a name="see-also"></a>Confira também
- [Tipos de projetos](../../extensibility/internals/project-types.md)
- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Amostras de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
