---
title: Objeto VSCodeWindowManager | Microsoft Docs
description: Saiba mais sobre o objeto VSCodeWindowManager, que é responsável pelo gerenciamento de adornos, por exemplo, a barra suspensa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5c602a1cf46382e5a8b5c688501b2406e4a6d0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863988"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar adornos (por exemplo, a barra suspensa). Para obter mais informações, consulte [Personalizando janelas de código usando a API herdada](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

A tabela a seguir mostra as interfaces no `VSCodeWindowManager` objeto.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite que adorners (como barras suspensas) sejam adicionados ou removidos de uma janela de código.|