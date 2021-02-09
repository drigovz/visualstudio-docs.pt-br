---
title: Referência de API não gerenciada (desenvolvimento do Office no Visual Studio)
description: A referência de API não gerenciada é usada para ajudar a carregar suplementos do VSTO gerenciados por carga. Você também pode criar seu próprio componente de carregador de suplemento do VSTO implementando essa interface.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cac9e2d01b47e0088543aeabcaeff30853314157
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908551"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referência de API não gerenciada (desenvolvimento do Office no Visual Studio)

A partir do sistema de Microsoft Office de 2007, os aplicativos do Office usam a interface de [interface IManagedAddin](../vsto/imanagedaddin-interface.md) para chamar um componente de carregador de suplemento do VSTO que está incluído no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Esse componente é usado para ajudar os suplementos do VSTO gerenciados por carga. Você pode criar seu próprio componente de carregador de suplemento do VSTO implementando essa interface.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Nesta seção

[Interface IManagedAddin](../vsto/imanagedaddin-interface.md)

Uma interface COM que você pode implementar para carregar e descarregar suplementos do VSTO gerenciados em aplicativos do Office.
