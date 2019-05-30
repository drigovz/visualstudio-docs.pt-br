---
title: Automação de configuração e objetos SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c9dc8012433f9ec73f15b9249f6b7ac08bdad7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347969"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação para objetos de configuração e SelectedItem

Você pode automatizar a compilação e os processos do item selecionado no Visual Studio.

## <a name="automation-for-builds"></a>Automação de compilações

Compilação ou a configuração tem um modelo de automação que é fornecido quando você implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obter mais informações, consulte [Compreender configurações de build](../../ide/understanding-build-configurations.md).

Se você criar um VSPackage e deseja controlar as opções de configuração, você deve usar o modelo de automação.

## <a name="automation-for-selecteditem"></a>Automação para SelectedItem

Você não precisa fornecer uma implementação para o `SelectedItem` porque o Visual Studio contém uma implementação padrão do objeto. No entanto, você pode implementar o `SelectedItem` objeto se você preferir. Você deve implementar um objeto que contém o `SelectedItem` da interface e retorna uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com `VSITEMID` definido como [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuir para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Compreender configurações de build](../../ide/understanding-build-configurations.md)