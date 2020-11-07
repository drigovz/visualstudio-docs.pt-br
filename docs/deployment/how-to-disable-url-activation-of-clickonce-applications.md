---
title: Desabilitar a ativação de URL de aplicativos ClickOnce
description: Saiba como desabilitar o início automático na instalação para seu aplicativo ClickOnce, caso você queira que os usuários iniciem o aplicativo no menu iniciar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 46e46278f5465de029aa9536744f51843397d743
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351226"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL

Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente imediatamente após ser instalado a partir de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e informar os usuários para iniciar o aplicativo no menu **Iniciar** em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.

Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário a partir de um servidor Web. Ele não pode ser usado para aplicativos somente online, que só podem ser iniciados usando sua URL. Para obter mais informações sobre a diferença entre aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Este procedimento usa a ferramenta SDK (Software Development Kit) do Windows MageUI.exe. Para obter mais informações sobre essa ferramenta, consulte [MageUI.exe (manifest Generation and Editing Tool, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Você também pode executar esse procedimento usando o Visual Studio.

## <a name="procedure"></a>Procedimento

### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo

1. Abra seu manifesto de implantação no MageUI.exe. Se você ainda não tiver criado uma, siga as etapas descritas em [Walkthrough: implantar manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Selecione a guia **Opções de implantação** .

3. Desmarque a caixa de seleção **Executar aplicativo automaticamente após a instalação** .

4. Salve e assine o manifesto.

## <a name="see-also"></a>Veja também

- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)