---
title: 'Como: usar a pesquisa no Designer de Fluxo de Trabalho | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659128"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Como: Use Pesquisa em Designer de Fluxo de Trabalho
Para facilitar a criação maior, os fluxos de trabalho mais complexos, pesquisam podem ser usados em Designer de Fluxo de Trabalho para localizar itens por palavras-chave. Observe que o designer não suporta substitui. Pesquisar encontrará a seguir no designer:

## <a name="quick-find"></a>Localização Rápida
 Localize rápido encontrará a seguir no designer:

- Propriedades de objetos de <xref:System.Activities.Activity> , de objetos, <xref:System.Activities.Statements.FlowNode> de objetos <xref:System.Activities.Statements.State> , das transições, e outros itens personalizados de controle de fluxo.

- Variáveis

- Arguments

- Expressões

#### <a name="using-quick-find"></a>Usar localizar rápido

1. Com o designer de fluxo de trabalho aberto, pressione **Ctrl + F**ou selecione **Editar**, **Localizar e substituir**, **localização rápida**.

2. Insira o termo de pesquisa na caixa de texto **Localizar** e clique em **Localizar próximo**.

3. O termo de pesquisa será localizado no fluxo de trabalho atual. A captura de tela a seguir mostra um nome para exibição de atividade que está sendo localizado no designer.

     ![Resultado da pesquisa no Designer de Fluxo de Trabalho](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Localizar nos arquivos
 Usar localize em arquivos permanecerá cadeias de caracteres nos arquivos de fluxo de trabalho, incluindo arquivos XAML.

#### <a name="using-find-in-files"></a>Usar localizar em arquivos

1. No Visual Studio, pressione **Ctrl + Shift + F**ou selecione **Editar**, **Localizar e substituir**, **localizar nos arquivos**

2. Insira o item de pesquisa na caixa de texto **Localizar** e clique em **Localizar tudo**

3. O resultado da localização será mostrado na exibição [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]**Localizar resultado** . Clicando duas vezes em um item de resultado navegará na atividade que contém a correspondência no designer de fluxo de trabalho.