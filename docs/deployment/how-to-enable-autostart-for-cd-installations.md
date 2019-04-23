---
title: 'Como: Habilitar o AutoStart para instalações por CD | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 66f5510ae63507aebb97a7f8bdfd3e367f1afc85
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074655"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como: Habilitar o Início Automático para instalações do CD
Ao implantar uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo por meio de uma mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo seja iniciado automaticamente quando a mídia for inserida.

 `AutoStart` pode ser habilitada na **Publish** página do **Designer de projeto**.

### <a name="to-enable-autostart"></a>Para habilitar o AutoStart

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. Clique o **publicar** guia.

3. Clique o **opções** botão.

     O **opções de publicação** caixa de diálogo é exibida.

4. Clique em **implantação**.

5. Selecione o **instalações para CD, iniciar automaticamente a instalação quando o CD é inserido** caixa de seleção.

     Uma *Autorun* arquivo será copiado para o local de publicação quando o aplicativo é publicado.

## <a name="see-also"></a>Consulte também
- [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)