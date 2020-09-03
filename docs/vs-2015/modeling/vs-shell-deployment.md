---
title: Implantação do VS Shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659313"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um shell isolado permite que você determine qual funcionalidade do Visual Studio você precisa para interagir com sua linguagem específica de domínio e como essa solução deve ser exibida. Para obter mais informações sobre o Shell isolado do Visual Studio, consulte [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md). Você pode encontrar mais informações sobre como personalizar o Shell isolado na [personalização do Shell isolado](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para definir um shell do Visual Studio como o destino de implantação

1. No projeto **DslPackage** , abra **Source.Extension.tt**.

2. Em `<SupportedProducts>` Inserir:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Substitua *MyIsolatedShell* pelo nome do seu pacote de shell isolado.
