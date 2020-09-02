---
title: Página Opções, Propriedades do Nó de Fontes e Cores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662422"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Página de Opções, Fontes e Cores, Propriedades de Nó
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este documento descreve as propriedades de fonte e de cor de uma janela de ferramentas registrada para ser exibida em **Fontes e Cores** na categoria **Ambiente** da caixa de diálogo **Opções**. Isso dá suporte à natureza dinâmica de grupos de itens de coloração, que poderão ser alterados se os VSPackages forem instalados ou desinstalados.

 A seção a seguir mostra um exemplo de um tipo de janela registrada e as propriedades disponíveis para cada janela.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor de Texto, impressora ou caixas de diálogo e janelas de ferramentas
 `DTE.Properties("FontsAndColors", "TextEditor")`

 - ou -

 `DTE.Properties("FontsAndColors", "Printer")`

 - ou -

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nome do item de propriedade|Valor|Descrição|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (Cadeia de Caracteres)|O nome da fonte a ser usado, como “Courier New”.|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Um valor de <xref:EnvDTE.vsFontCharSet>, especificando o tipo de conjunto de caracteres a ser usado, como hebraico ou russo.|
|FontSize|Get/Set (Curto)|O tamanho da fonte a ser usado, em pontos. Por exemplo, 10 ou 12.|

## <a name="see-also"></a>Consulte Também
 [Controlando as configurações de opções](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [que determinam os nomes dos itens de propriedade na página opções de páginas](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) opções, página opções de nó de [ambiente](../../ide/reference/options-page-environment-node-properties.md) [, propriedades do nó do editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)
