---
title: Estendendo projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d31da41e3be73f4e2e036841bfc1d96f4476e856
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695408"
---
# <a name="extend-projects"></a>Estender projetos
Projetos e soluções são as maneiras em que o Visual Studio organiza os arquivos de código e recursos em unidades de compilação e implantação. Você pode encontrar mais informações sobre projetos de [projetos (SDK do Visual Studio)](../extensibility/extending-projects.md).

 Você pode criar seus próprios tipos de projeto com o SDK do Visual Studio e a estrutura de pacote gerenciado para projetos, que pode ser baixado em [estrutura de pacote gerenciado para projetos](https://github.com/tunnelvisionlabs/MPFProj10). Para entender como os projetos personalizados são implementados, consulte [nova geração de projeto: Nos bastidores, parte um](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nova geração de projeto: Nos bastidores, parte dois](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Os tópicos nesta seção descrevem como criar projetos personalizados e como gerenciar diferentes tipos de solução do Visual Studio.

## <a name="in-this-section"></a>Nesta seção
- [Criar um sistema de projeto básico, parte 1](../extensibility/creating-a-basic-project-system-part-1.md) descreve como criar um sistema de projeto personalizado.

- [Criar um sistema de projeto básico, parte 2](../extensibility/creating-a-basic-project-system-part-2.md) descreve como criar um sistema de projeto personalizado.

- [Salvar dados em arquivos de projeto](../extensibility/saving-data-in-project-files.md) Explains como adicionar ao projeto (<em>.</em> proj *) os arquivos.

- [Verificar subtipos de um projeto em tempo de execução](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) explica como verificar o subtipo de um projeto em tempo de execução.

- [Adicionar e remover as páginas de propriedade](../extensibility/adding-and-removing-property-pages.md) explica como personalizar as páginas de propriedades para o seu projeto personalizado.

- [Adicionar um atributo a um item de projeto](../extensibility/adding-an-attribute-to-a-project-item.md) explica como adicionar um atributo a um item de projeto personalizado.

- [Manter a propriedade de um item de projeto](../extensibility/persisting-the-property-of-a-project-item.md) explica como persistir as propriedades de um item de projeto personalizado.

- [Gerenciar projetos universais do Windows](../extensibility/managing-universal-windows-projects.md) explica como gerenciar projetos universais.