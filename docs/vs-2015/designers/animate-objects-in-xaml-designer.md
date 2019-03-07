---
title: Animar objetos no Designer XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7846ade8dba2ce849acf62311e508c157b07dd3e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54805503"
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos no XAML Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível criar animações curtas que movem objetos ou fazer com que eles esmaeçam.  
  
 Para começar, crie um *storyboard*. Um storyboard contém uma ou mais *linhas do tempo*. Defina os *quadros chave* em uma linha do tempo para marcar as alterações de propriedade. Depois, ao executar a animação, o Blend interpolará as alterações de propriedade durante o período de tempo designado. O resultado é uma transição suave. É possível animar qualquer propriedade que pertença a um objeto, mesmo propriedades não visuais.  
  
 A ilustração a seguir mostra um storyboard denominado **MoveUp**. A linha do tempo contém quadros chave que marcam as posições X e Y de um retângulo. Quando essa animação é executada, o retângulo move de uma posição para outra sem problemas.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Saiba como criar animações assistindo a esses vídeos.  
  
|Assista a um breve vídeo:|Saiba como:|  
|--------------------------|-------------------|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar linhas do tempo](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Crie uma linha do tempo e trabalhe com objetos nela.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Adicionar quadros chave e repetir a animação](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Adicione quadros chave e defina propriedades em cada um deles. Em seguida, execute a animação e assista à transição suave entre os objetos.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Adicionar gatilhos de evento para obter interatividade](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Inicie uma animação quando ocorrer um evento. Por exemplo, inicie uma animação quando a janela for carregada.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Animar cores](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Use uma animação para alterar a cor de um objeto.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar e modificar trajetórias de animação](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Anime objetos ao longo de um caminho.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Suavizar quadros chave](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Aumente ou diminua a velocidade de uma animação no início (*suavização de entrada*) ou no final (*suavização de saída*) de uma animação.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Animar o botão](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Crie efeitos interessantes que aparecem em um botão quando o usuário aponta para ele.|  
|![Configurar Recursos Instalados](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon")[Criar animação e trabalhar com a suavização](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Anime efeitos que aparecem quando um usuário pressiona um botão na imagem de uma calculadora.|  
  
## <a name="see-also"></a>Consulte também  
 [Criando uma interface do usuário usando o Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
