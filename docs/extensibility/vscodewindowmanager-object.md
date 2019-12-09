---
title: Objeto VSCodeWindowManager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c67fb719c6ec87e7707a406e2e7f67cd71569b39
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189039"
---
# <a name="vscodewindowmanager-object"></a>Objeto VSCodeWindowManager

O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar adornos (por exemplo, a barra suspensa). Para obter mais informações, consulte [Personalizando janelas de código usando a API herdada](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

A tabela a seguir mostra as interfaces no objeto `VSCodeWindowManager`.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Permite que adorners (como barras suspensas) sejam adicionados ou removidos de uma janela de código.|