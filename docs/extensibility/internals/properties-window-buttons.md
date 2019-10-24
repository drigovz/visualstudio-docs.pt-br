---
title: Botões da janela Propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725264"
---
# <a name="properties-window-buttons"></a>Botões da janela Propriedades
Dependendo da linguagem de desenvolvimento e do tipo de produto, determinados botões são exibidos por padrão na barra de ferramentas da janela **Propriedades** . Em todos os casos, os botões **Categorizado**, em **ordem alfabética**, **Propriedades**e **páginas de propriedades** são exibidos. No Visual C# e Visual Basic, o botão **eventos** também é exibido. Em determinados projetos C++ visuais, as **mensagens do vc + +** e os botões de **substituições do vc** são exibidos. Botões adicionais podem ser exibidos para outros tipos de projeto. Para obter mais informações sobre os botões na janela **Propriedades** , consulte [janela Propriedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementação de botões da janela Propriedades
 Quando você clica no botão **Categorizado** , o Visual Studio chama a interface <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> no objeto que tem o foco para classificar suas propriedades por categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> é implementado no objeto `IDispatch` que é apresentado à janela **Propriedades** .

 Há 11 categorias de propriedades predefinidas, que têm valores negativos. Você pode definir categorias personalizadas, mas é recomendável atribuí-las a valores positivos para diferenciá-las das categorias predefinidas.

 O método <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> retorna o valor da categoria de propriedade apropriado para a propriedade especificada. O método <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> retorna uma cadeia de caracteres que contém o nome da categoria. Você só precisa fornecer suporte para valores de categoria personalizados porque o Visual Studio conhece os valores de categoria de propriedade padrão.

 Quando você clica no botão em **ordem alfabética** , as propriedades são exibidas em ordem alfabética por nome. Os nomes são recuperados por `IDispatch` de acordo com um algoritmo de classificação localizado.

 Quando a janela **Propriedades** estiver aberta, o botão **Propriedades** será mostrado automaticamente como selecionado. Em outras partes do ambiente, o mesmo botão é exibido e você pode clicar nele para mostrar a janela **Propriedades** .

 O botão **páginas de propriedades** não estará disponível se `ISpecifyPropertyPages` não for implementada para o objeto selecionado. As páginas de propriedades exibem propriedades dependentes da configuração que normalmente são associadas a soluções e projetos, mas também podem ser associadas a itens de projeto (por exemplo C++, no Visual).

> [!NOTE]
> Não é possível adicionar botões da barra de ferramentas à janela **Propriedades** usando código não gerenciado. Para adicionar um botão da barra de ferramentas, você deve criar um objeto gerenciado que derive de <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Consulte também
- [Estender as propriedades](../../extensibility/internals/extending-properties.md)