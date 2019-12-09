---
title: Depuração e o processo de hospedagem | Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188461"
---
# <a name="debugging-and-the-hosting-process"></a>Depuração e o processo de hospedagem
O processo de hospedagem do Visual Studio melhora o desempenho do depurador e habilita novos recursos do depurador, como a depuração de confiança parcial e a avaliação de expressão de tempo de design. Você pode desabilitar o processo de hospedagem se isso for necessário. As seções a seguir descrevem algumas diferenças entre a depuração com e sem o processo de hospedagem.

> [!NOTE]
> A partir do Visual Studio 2017, a opção de depurar usando o processo de hospedagem não é mais necessária e foi removida. Para obter mais informações, consulte [depuração: o Visual Studio 2017 visa acelerar seu trabalho menos favorito](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx).

## <a name="partial-trust-debugging-and-click-once-security"></a>Depuração de confiança parcial e segurança de Click-Once
 A depuração de confiança parcial requer o processo de hospedagem. Se você desabilitar o processo de hospedagem, a depuração de confiança parcial não funcionará mesmo que a segurança de confiança parcial esteja habilitada na página **Segurança** de **Propriedades do Projeto**. Para obter mais informações, consulte [como: Depurar um aplicativo de confiança parcial](debugger-security.md).

## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design
 A expressão de tempo de design sempre usa o processo de hospedagem. Desabilitar o processo de hospedagem em **Propriedades do Projeto** desabilita a avaliação de expressão de tempo de design para projetos de biblioteca de classes. Para outros tipos de projeto, a avaliação de expressão de tempo de design não é desabilitada. Em vez disso, o Visual Studio inicia o executável real e usa-o para a avaliação de tempo de design sem o processo de hospedagem. Essa diferença pode produzir resultados diferentes.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Diferenças de AppDomain.CurrentDomain.FriendlyName
 O `AppDomain.CurrentDomain.FriendlyName` retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `AppDomain.CurrentDomain.FriendlyName` com o processo de hospedagem habilitado, ele retornará *app_name*`.vhost.exe`. Se você chamá-lo do processo de hospedagem desabilitado, ele retornará *app_name*`.exe`.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Diferenças de Assembly.GetCallingAssembly().FullName
 O `Assembly.GetCallingAssembly().FullName` retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem habilitado, ele retornará `mscorlib`. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem desabilitado, ele retornará o nome do aplicativo.

## <a name="see-also"></a>Consulte também

- [Como depurar um aplicativo parcialmente confiável](debugger-security.md)