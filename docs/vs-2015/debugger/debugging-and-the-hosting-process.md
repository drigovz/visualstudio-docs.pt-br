---
title: Depuração e o processo de hospedagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925417"
---
# <a name="debugging-and-the-hosting-process"></a>Depuração e o processo de hospedagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O processo de hospedagem do Visual Studio melhora o desempenho do depurador e habilita novos recursos do depurador, como a depuração de confiança parcial e a avaliação de expressão de tempo de design. Você pode desabilitar o processo de hospedagem se isso for necessário. Para obter mais informações, confira [Como: Desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md). As seções a seguir descrevem algumas diferenças entre a depuração com e sem o processo de hospedagem.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Depuração de confiança parcial e segurança de Click-Once  
 A depuração de confiança parcial requer o processo de hospedagem. Se você desabilitar o processo de hospedagem, a depuração de confiança parcial não funcionará mesmo que a segurança de confiança parcial esteja habilitada na página **Segurança** de **Propriedades do Projeto**. Para obter mais informações, confira [Como: Desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md) e [como: Depurar aplicativos de confiança parcial](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design  
 A expressão de tempo de design sempre usa o processo de hospedagem. Desabilitar o processo de hospedagem em **Propriedades do Projeto** desabilita a avaliação de expressão de tempo de design para projetos de biblioteca de classes. Para outros tipos de projeto, a avaliação de expressão de tempo de design não é desabilitada. Em vez disso, o Visual Studio inicia o executável real e usa-o para a avaliação de tempo de design sem o processo de hospedagem. Essa diferença pode produzir resultados diferentes.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Diferenças de AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` retorna resultados diferentes quando o processo de hospedagem está habilitado. Se você chamar `AppDomain.CurrentDomain.FriendlyName` com o processo de hospedagem habilitado, ele retornará *app_name*`.vhost.exe`. Se você chamá-lo o processo de hospedagem desabilitado, ele retornará *app_name*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Diferenças de Assembly.GetCallingAssembly().FullName  
 `Assembly.GetCallingAssembly().FullName` retorna resultados diferentes quando o processo de hospedagem está habilitado. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem habilitado, ele retornará `mscorlib`. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem desabilitado, ele retornará o nome do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Processo de hospedagem (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Como: Depurar um aplicativo de confiança parcial](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Como: desabilitar o processo de host](../ide/how-to-disable-the-hosting-process.md)
