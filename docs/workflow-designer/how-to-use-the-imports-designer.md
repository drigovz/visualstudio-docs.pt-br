---
title: 'Designer de Fluxo de Trabalho-como: usar o designer de importações'
description: Saiba como o designer de importações permite inserir namespaces para os tipos que serão usados em suas expressões.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd736c01843d746ee43a82e6bb6f5239da1c660e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894043"
---
# <a name="how-to-use-the-imports-designer"></a>Como: Use o designer imports

O designer imports permite que você inserir em namespaces para os tipos que você usará em suas expressões. Assim como as **importações** ou o **uso** de palavras-chave em Visual Basic e C#, a especificação de namespaces no designer de importações permite que você simplesmente Insira um nome de tipo em sua expressão em vez de um nome de tipo de versão totalmente qualificado.

O designer imports reage a alterações na interface do usuário e as alterações feitas quando o fluxo de trabalho é salvo. Quando o fluxo de trabalho é salvo, namespaces podem ser adicionados automaticamente ao designer imports. Elas incluem o seguinte:

- Namespaces para alguns tipos usados em declarações de variável e argumento.

- Namespaces para alguns tipos usados em expressões.

- Algumas outras namespaces necessárias para serializar o fluxo de trabalho (por exemplo, namespaces usadas por atividades personalizados soltas no fluxo de trabalho).

  Quando o fluxo de trabalho é salvo, você pode notar que algumas namespaces que você excluiu manualmente que são adicionados automaticamente ao designer imports devido à lógica descrita na lista anterior.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Para adicionar um namespace à lista de namespaces importados

1. Abra um aplicativo de serviço de fluxo de trabalho do WCF, aplicativo de console de fluxo de trabalho ou projeto de biblioteca de atividades no Visual Studio ou um aplicativo de fluxo de trabalho rehospedado.

2. Clique em **importações** na parte inferior da tela principal. O designer imports aparecerá.

3. Insira ou selecione em um namespace do controle de lista suspensa na parte superior do designer imports.

     Enquanto você digita, uma lista de namespaces válidas que correspondem aos caracteres tipados aparece.

4. Pressione **Enter** para adicionar o namespace à lista.

5. Se você quiser remover um namespace da lista, selecione o namespace e pressione a tecla **delete** no teclado. Observe que um namespace só pode ser excluída se o namespace não é válido por algum motivo, por exemplo se o assembly que contém o namespace não é referenciado pelo projeto.
