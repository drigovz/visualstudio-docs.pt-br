---
title: 'Como: Instalar um visualizador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e223831b30f784094a2affa5cebb314cc6e997f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059702"
---
# <a name="how-to-install-a-visualizer"></a>Como: Instalar um visualizador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Instalar um visualizador é um processo simples.  
  
> [!NOTE]
>  Na **Store** aplicativos, somente o texto padrão, os visualizadores HTML, XML e JSON são suportados. Não há suporte para visualizadores personalizados (criados pelo usuário).  
  
### <a name="to-install-a-visualizer"></a>Para instalar um visualizador  
  
1. Localize a DLL que contém o visualizador que você criou.  
  
2. Copie a DLL para qualquer um dos seguintes locais:  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.  
  
4. Reinicie a sessão de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Como: Escrever um visualizador](../debugger/how-to-write-a-visualizer.md)
