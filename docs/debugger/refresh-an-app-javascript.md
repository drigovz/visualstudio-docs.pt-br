---
title: Atualizar um aplicativo UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 43f232157ef9237ba9d401f473ab0db1b1260f40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828716"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Atualizar um aplicativo UWP no Visual Studio
  
 Você pode fazer alterações ao seu código enquanto você está depurando e, em seguida, atualizar um aplicativo UWP usando JavaScript escolhendo o **atualizar o Windows app** botão a **depurar** barra de ferramentas. Dessa forma, o aplicativo é recarregado sem parar e reiniciar o depurador. A funcionalidade Atualizar permite que você modifique o código HTML, CSS e JavaScript e veja rapidamente o resultado. Esse recurso tem suporte para aplicativos UWP.  
  
 A atualização não mantém o estado do aplicativo nem reflete as seguintes alterações feitas no aplicativo:  
  
-   Alterações no arquivo de manifesto do pacote, inclusive nas imagens especificadas no manifesto do pacote.  
  
-   Alterações em referências, como a adição ou a remoção de uma referência de SDK, ou alterações nos componentes do Windows Runtime  (arquivos .winmd).  
  
-   Alterações em recursos, como as efetuadas nas cadeias de caracteres dos arquivos .resjson.  
  
-   Alterações em arquivos de projeto que resultam em mudanças de nome de caminho, novos arquivos de projeto ou arquivos excluídos.  
  
-   Alterações em propriedades de projetos e de itens, como as feitas no dispositivo de depuração selecionado, ou alterações na ação de pacote para um arquivo (na janela Propriedades).  
  
> [!IMPORTANT]
>  Ao alterar referências, alterar o manifesto do pacote ou fazer outras alterações especificadas na lista anterior, você precisa interromper e reiniciar o depurador para atualizar os arquivos de origem HTML, CSS e JavaScript.  
  
### <a name="to-refresh-an-app"></a>Para atualizar um aplicativo  
  
1.  Com o seu projeto UWP aberto no Visual Studio, selecione **computador Local** como o destino de depuração.
  
     ![Lista de destino de depuração Select](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Pressione F5 para executar o aplicativo no modo de depuração.  
  
4.  Alterne para o Visual Studio. 
  
5.  Na home page do seu aplicativo UWP, edite algumas de HTML.
  
7.  Clique no botão Atualizar aplicativo do Windows **, que tem esta aparência:** . ![Atualizar o botão de aplicativo do Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Ou pressione F4.)  
  
8.  Altere para o aplicativo. O aplicativo é recarregado e o HTML atualizado é usado para renderizar o aplicativo.
  
## <a name="see-also"></a>Consulte também  
 [Início Rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)