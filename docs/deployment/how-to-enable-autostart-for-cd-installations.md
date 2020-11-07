---
title: Habilitar a inicialização automática para instalações de CD | Microsoft Docs
description: Saiba como habilitar o AutoStart ao implantar um aplicativo ClickOnce por meio de mídia removível, como CD-ROM ou DVD-ROM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6ed3df72b98454c4669e7d9bcd21c0612a6fef3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349952"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como habilitar o Início Automático para instalações por CD
Ao implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo por meio de mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo seja iniciado automaticamente quando a mídia for inserida.

 `AutoStart` pode ser habilitado na página **publicar** do designer de **projeto**.

### <a name="to-enable-autostart"></a>Para habilitar o AutoStart

1. Com um projeto selecionado no **Gerenciador de Soluções** , no menu **Projeto** , clique em **Propriedades**.

2. Clique na guia **Publicar**.

3. Clique no botão **Opções** .

     A caixa de diálogo **Opções de publicação** é exibida.

4. Clique em **Implantação**.

5. Marque a caixa **de seleção para instalações de CD, iniciar a instalação automaticamente quando o CD for inserido** .

     Um arquivo *autorun. inf* será copiado para o local de publicação quando o aplicativo for publicado.

## <a name="see-also"></a>Veja também
- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)