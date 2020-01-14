---
title: Hierarquias no Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08005b69a1af16b07212cb29547875fad89e1d6a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848948"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarquias no Visual Studio
O ambiente de desenvolvimento integrado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) exibe um projeto como uma *hierarquia*. No IDE, uma hierarquia é uma árvore de nós, em que cada nó tem um conjunto de propriedades associadas. Uma *hierarquia de projeto* é um contêiner que contém os itens do projeto, as relações dos itens e as propriedades e os comandos associados aos itens.

 No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você gerencia hierarquias de projeto usando a interface de hierarquia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. A interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> redireciona os comandos que você invoca dos itens de projeto para a janela de hierarquia apropriada em vez do manipulador de comandos padrão.

## <a name="project-hierarchies"></a>Hierarquias de projeto
 Cada hierarquia de projeto contém itens que você pode exibir e editar. Esses itens variam de acordo com o tipo de projeto. Por exemplo, um projeto de banco de dados pode conter procedimentos armazenados, exibições de banco de dados e tabelas de banco de dados. Um projeto de linguagem de programação, por outro lado, provavelmente incluirá arquivos de origem e arquivos de recursos para bitmaps e caixas de diálogo. As hierarquias podem ser aninhadas, o que oferece uma flexibilidade adicional quando você cria uma hierarquia de projeto.

 Quando você cria um novo tipo de projeto, o tipo de projeto controla o conjunto completo de itens que podem ser editados nele. No entanto, os projetos podem conter itens para os quais não têm suporte para edição. Por exemplo, os C++ projetos visuais podem conter arquivos HTML, embora o C++ Visual não forneça nenhum editor personalizado para o tipo de arquivo HTML.

 As hierarquias gerenciam a persistência dos itens que elas contêm. A implementação da hierarquia deve controlar todas as propriedades especiais que afetam a persistência dos itens dentro da hierarquia. Por exemplo, se os itens representam objetos em um repositório em vez de arquivos, a implementação da hierarquia deve controlar a persistência desses objetos. O IDE em si direciona a hierarquia para salvar os itens em conformidade com a entrada do usuário, mas o IDE não controla as ações necessárias para salvar esses itens. Em vez disso, o projeto está no controle.

 Quando um usuário abre um item em um editor, a hierarquia que controla esse item é selecionada e torna-se a hierarquia ativa. A hierarquia selecionada determina o conjunto de comandos disponíveis para agir no item. Controlar o foco do usuário dessa maneira permite que a hierarquia reflita o contexto atual do usuário.

## <a name="see-also"></a>Veja também
- [Tipos de projeto](../../extensibility/internals/project-types.md)
- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Exemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
