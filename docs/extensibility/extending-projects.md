---
title: Ampliação de Projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711744"
---
# <a name="extend-projects"></a>Ampliar projetos
Projetos e soluções são as maneiras pelas quais o Visual Studio organiza arquivos de código e recursos em unidades de compilação e implantação. Você pode encontrar mais informações sobre projetos em [Projetos (Visual Studio SDK)](../extensibility/extending-projects.md).

 Você pode criar seus próprios tipos de projeto com o Visual Studio SDK e o Managed Package Framework for Projects, que você pode baixar no [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Para entender como os projetos personalizados são implementados, consulte [Nova geração de projetos: Sob o capô, parte um](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e Nova geração de [projetos: Sob o capô, parte dois](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Os tópicos desta seção descrevem como criar projetos personalizados e como gerenciar diferentes tipos de solução visual studio.

## <a name="in-this-section"></a>Nesta seção
- [Crie um sistema básico de projeto, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) Descreve como criar um sistema de projeto personalizado.

- [Crie um sistema básico de projeto, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) Descreve como criar um sistema de projeto personalizado.

- [Salvar dados em arquivos de projeto](../extensibility/saving-data-in-project-files.md) Explica como adicionar ao projeto (<em>.</em> proj*) arquivos.

- [Verificar subtipos de um projeto em tempo de execução](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) Explica como verificar o subtipo de um projeto em tempo de execução.

- [Adicionar e remover páginas de propriedade](../extensibility/adding-and-removing-property-pages.md) Explica como personalizar as páginas de propriedade para o seu projeto personalizado.

- [Adicionar um atributo a um item de projeto](../extensibility/adding-an-attribute-to-a-project-item.md) Explica como adicionar um atributo a um item de projeto personalizado.

- [Persistir a propriedade de um item de projeto](../extensibility/persisting-the-property-of-a-project-item.md) Explica como persistir as propriedades de um item de projeto personalizado.

- [Gerenciar projetos universais do Windows](../extensibility/managing-universal-windows-projects.md) Explica como gerenciar projetos universais.
