---
title: Metadados como fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b1d96224be13a12dcaadb394584f8441c7bd1934
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667519"
---
# <a name="metadata-as-source"></a>Metadados como origem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metadados como fonte permitem que você exiba metadados que aparecem como C# código-fonte em um buffer somente leitura. Isso permite uma exibição das declarações dos tipos e Membros (sem implementações). Você pode exibir os metadados como origem executando o comando **go to Definition** para tipos ou membros cujo código-fonte não está disponível no seu projeto ou solução.

> [!NOTE]
> Quando você tenta executar o comando **go to Definition** para tipos ou membros marcados como internos, o IDE (ambiente de desenvolvimento integrado) não exibe seus metadados como origem, independentemente de o assembly de referência ser um amigo ou não.

 Você pode exibir metadados como origem no editor de código ou na janela de **definição de código** .

## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Exibindo metadados como fonte no editor de códigos
 Quando você executa o comando **go to Definition** para um item cujo código-fonte não está disponível, um documento com guias que contém uma exibição dos metadados desse item, exibido como fonte, aparece no editor de código. O nome do tipo, seguido por **[de metadados]** , aparece na guia do documento.

 Por exemplo, se você executar o comando **go to Definition** para <xref:System.Console>, os metadados de <xref:System.Console> aparecerão no editor de C# código como código-fonte que se assemelha a sua declaração, mas sem uma implementação.

 ![Metadados como origem](../csharp-ide/media/metadatasource.png "Metadataização")

## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Exibindo metadados como origem na janela de definição de código
 Quando a janela de **definição de código** está ativa ou visível, o IDE executa automaticamente o comando **go to Definition** para itens sob o cursor no editor de códigos e para itens que são selecionados em **modo de exibição de classe** ou no **pesquisador de objetos**. Se o código-fonte não estiver disponível para esse item, o IDE exibirá os metadados do item como origem na janela de **definição de código** .

 Por exemplo, se você colocar o cursor dentro da palavra <xref:System.Console> no editor de código, os metadados de <xref:System.Console> aparecerão como fonte na janela de **definição de código** . A origem é semelhante à declaração de <xref:System.Console>, mas sem uma implementação.

 Se você quiser ver a declaração de um item que aparece na janela de **definição de código** , clique com o botão direito do mouse no item e clique em **ir para definição**.