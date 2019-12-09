---
title: Caixa de diálogo Configurações de Segurança Avançadas
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1fcc3d09e43fc5358cbe507c5045c16cc9f8cf9
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461857"
---
# <a name="advanced-security-settings-dialog-box"></a>Caixa de diálogo Configurações de Segurança Avançadas

Essa caixa de diálogo permite especificar configurações de segurança relacionadas à depuração na zona.

![Caixa de diálogo Configurações de Segurança Avançada no Visual Studio](../media/advanced-security-settings.png)

Para acessar essa caixa de diálogo, selecione um nó do projeto no **Gerenciador de Soluções** e, no menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Segurança**. Na página **Segurança** página, selecione **Habilitar Configurações de Segurança do ClickOnce**, clique em **Este é um aplicativo de confiança parcial** e, em seguida, clique em **Avançado**.

## <a name="uielement-list"></a>Lista UIElement

**Conceder ao aplicativo acesso ao site de origem**

Se você marcar esta caixa de seleção, o aplicativo poderá acessar o site da Web ou o compartilhamento do servidor no qual ele é publicado. Por padrão, essa opção é selecionada.

**Depurar este aplicativo como se ele tivesse sido baixado da seguinte URL**

Se você precisar permitir que o aplicativo acesse o site ou o compartilhamento do servidor correspondente à **URL de Instalação** especificada na página **Publicar**, insira a URL aqui. Essa opção está disponível apenas quando **Conceder ao aplicativo acesso ao site de origem** está selecionado.

## <a name="see-also"></a>Consulte também

- [Página Segurança, Designer de Projeto](../../ide/reference/security-page-project-designer.md)