---
title: Grade de exibição de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706184"
---
# <a name="properties-display-grid"></a>Grade de exibição de propriedades

A janela **Propriedades** exibe campos dentro de uma grade. A coluna à esquerda contém os nomes da propriedade; a coluna direita contém os valores de propriedade.

## <a name="work-with-the-grid"></a>Trabalhe com a grade

A lista de duas colunas mostra propriedades independentes de configuração que podem ser alteradas na hora do design e suas configurações atuais. Observe que todas as propriedades podem não ser mostradas. Uma propriedade pode ser definida como oculta, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> por exemplo, implementando o método. Especificamente, para ocultar propriedades que tenham propriedades de crianças:

1. Defina `pfDisplay` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> parâmetro `FALSE`em .

2. Defina `pfHide` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> parâmetro `TRUE`em .

Para empurrar as informações para a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>janela **Propriedades,** o IDE usa . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é chamado por VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a serem exibidas na janela **Propriedades.** **A**implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` chamadas do Solution Explorer usando [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) na hierarquia do projeto para adquirir os objetos navegáveis na hierarquia.

Se o seu VSPackage não suportar [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), o IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> tenta usar o valor para [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que o item de hierarquia ou itens forneçam.

O projeto VSPackage não <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> precisa ser criado porque o pacote de janela fornecido pelo IDE que o implementa (por exemplo, **O Solution Explorer)** constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> em seu nome.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>consiste em três métodos que são chamados pelo IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contém o número de objetos selecionados para serem exibidos na janela **Propriedades.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>retorna `IDispatch` os objetos selecionados para serem exibidos na janela **Propriedades.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>permite que qualquer um dos objetos devolvidos seja <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> selecionado pelo usuário. Isso permite que o VSPackage atualize visualmente a seleção exibida para o usuário na ui.

A janela **Propriedades** extrai `IDispatch` informações dos objetos para recuperar as propriedades que estão sendo navegadas. O navegador `IDispatch` Propriedades usa para perguntar ao objeto quais `ITypeInfo`propriedades ele suporta `IDispatch::GetTypeInfo`consultando , que é obtido a partir de . Em seguida, o navegador usa esses valores para preencher a janela **Propriedades** e alterar os valores para propriedades individuais exibidas na grade. As informações das propriedades são mantidas dentro do próprio objeto.

Como os objetos `IDispatch`retornados suportam, o chamador pode obter `IDispatch::Invoke` `ITypeInfo::Invoke` informações como o nome do objeto ligando para um ou com um identificador de despacho predefinido (DISPID) que representa as informações desejadas. Os DISPIDs declarados são negativos para garantir que eles não entrem em conflito com os identificadores definidos pelo usuário.

A janela **Propriedades** exibe diferentes tipos de campos, dependendo dos atributos de propriedades específicas de um objeto selecionado. Esses campos incluem caixas de edição, listas de paradas e links para caixas de diálogo de editor personalizados.

- Os valores contidos em uma lista <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> enumerada são recuperados por uma consulta para `IDispatch`. Os valores obtidos a partir de uma lista enumerada podem ser alterados na grade de propriedades clicando duas vezes no nome do campo ou clicando no valor e selecionando o novo valor da lista suspensa. Para propriedades que tenham configurações predefinidas a partir de listas enumeradas, clique duas vezes no nome da propriedade nos ciclos de lista Propriedades através das opções disponíveis. Para propriedades predefinidas com apenas duas opções, como true/false, clique duas vezes no nome da propriedade para alternar entre as escolhas.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`for, indicando que o valor foi alterado, o valor é exibido em texto em negrito. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>é usado para determinar se o valor pode ser redefinido para o valor original. Se assim for, você pode alterar de volta para o padrão clicando com o botão direito do mouse no valor e escolhendo **Redefinir** no menu exibido. Caso contrário, você tem que alterar o valor de volta para o padrão manualmente. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>também permite localizar e ocultar os nomes das propriedades exibidas durante o tempo de projeto, mas não afeta os nomes de propriedade exibidos durante o tempo de execução.

- Clicando no botão ellipsis (...) exibe uma lista de valores de propriedade a partir dos quais o usuário pode selecionar (como um seletor de cores ou uma lista de fontes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>fornece esses valores.

## <a name="see-also"></a>Confira também

- [Estender propriedades](../../extensibility/internals/extending-properties.md)
