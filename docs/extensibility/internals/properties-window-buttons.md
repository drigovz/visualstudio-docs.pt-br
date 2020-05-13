---
title: Botões de janela de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706169"
---
# <a name="properties-window-buttons"></a>Botões da janela Propriedades
Dependendo da linguagem de desenvolvimento e do tipo de produto, certos botões são exibidos por padrão na barra de ferramentas para a janela **Propriedades.** Em todos os casos, são exibidos os botões **Categorizado,** **Alfabetizado,** **Propriedades**e **Páginas de Propriedade.** No Visual C# e visual basic, o botão **Eventos** também é exibido. Em certos projetos Visuais C++, as **mensagens VC++** e os botões **VC Overrides** são exibidos. Botões adicionais podem ser exibidos para outros tipos de projeto. Para obter mais informações sobre botões na janela **Propriedades,** consulte [Janela propriedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementação de botões de janela de propriedades
 Quando você clica no botão **Categorizado,** o Visual Studio chama a <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interface no objeto que tem foco para classificar suas propriedades por categoria. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>é implementado `IDispatch` no objeto apresentado na janela **Propriedades.**

 Existem 11 categorias de propriedades predefinidas, que têm valores negativos. Você pode definir categorias personalizadas, mas recomendamos que você lhes atribua valores positivos para distingui-los das categorias predefinidas.

 O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método devolve o valor da categoria de propriedade apropriada para a propriedade especificada. O <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método retorna uma seqüência que contém o nome da categoria. Você só precisa fornecer suporte para valores de categoria personalizados porque o Visual Studio conhece os valores padrão da categoria de propriedade.

 Quando você clica no botão **Alfabeto,** as propriedades são exibidas em ordem alfabética pelo nome. Os nomes são `IDispatch` recuperados de acordo com um algoritmo de classificação localizado.

 Quando a janela **Propriedades** é aberta, o botão **Propriedades** é mostrado automaticamente como selecionado. Em outras partes do ambiente, o mesmo botão é exibido e você pode clicar nele para mostrar a janela **Propriedades.**

 O botão Páginas de `ISpecifyPropertyPages` **propriedade** não está disponível se não for implementado para o objeto selecionado. Páginas de propriedades exibem propriedades dependentes da configuração que normalmente estão associadas a soluções e projetos, mas também podem ser associadas a itens de projeto (por exemplo, no Visual C++).

> [!NOTE]
> Não é possível adicionar botões de barra de ferramentas à janela **Propriedades** usando código não gerenciado. Para adicionar um botão de barra de ferramentas, você <xref:System.Windows.Forms.Design.PropertyTab>deve criar um objeto gerenciado que deriva de .

## <a name="see-also"></a>Confira também
- [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
