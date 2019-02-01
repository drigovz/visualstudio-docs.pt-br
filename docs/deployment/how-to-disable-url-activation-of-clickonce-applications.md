---
title: 'Como: Desabilitar a ativação de aplicativos ClickOnce pela URL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdadf92fa94efe0a08fdf090e5a295e2f65096
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999971"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Como: Desabilitar a ativação de URL de aplicativos ClickOnce

Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente, imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.

Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Este procedimento usa a ferramenta Windows Software Development Kit (SDK) MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Você também pode executar esse procedimento usando o Visual Studio.

## <a name="procedure"></a>Procedimento

### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo

1.  Abra o manifesto de implantação no MageUI.exe. Se você não ainda tiver criado uma, siga as etapas em [passo a passo: Implantar manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2.  Selecione o **opções de implantação** guia.

3.  Desmarque a **executar o aplicativo depois de instalar automaticamente** caixa de seleção.

4.  Salve e assinar o manifesto.

## <a name="see-also"></a>Consulte também

- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)