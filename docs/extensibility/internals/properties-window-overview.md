---
title: Visão geral da janela de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706026"
---
# <a name="properties-window-overview"></a>Visão geral da janela Propriedades
A janela **Propriedades** é usada para exibir propriedades para objetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] selecionados nos dois principais tipos de janelas disponíveis no ambiente de desenvolvimento integrado (IDE). Estes dois tipos de janelas são:

- Janelas de ferramentas como Solution Explorer, Class View e Object browser

- Janelas de documentos contendo editores e designers como o designer de formulários, editor XML e editor HTML

## <a name="using-the-properties-window"></a>Usando a janela propriedades
 A janela **Propriedades** exibe as propriedades de itens únicos ou múltiplos selecionados. Se vários itens forem selecionados, será exibida a intersecção de todas as propriedades para todos os objetos selecionados.

 Eventos relacionados a um objeto selecionado dentro de uma janela de design de formulário ou editor HTML usando metadados COM+ são exibidos na janela **Propriedades.** Por exemplo, você pode selecionar um botão e `OnClick` exibir seus eventos associados, como um evento, que pode ser vinculado a esse botão.

 Os eventos exibidos na janela **Propriedades** são usados principalmente com objetos vinculados ao código. Se você estiver editando um formato de arquivo que não tem nada a ver com código, você não terá nenhum evento. Os eventos só são exibidos na janela **Propriedades** quando há uma vinculação entre código de execução e certos eventos associados a objetos específicos. Um exemplo disso seria o código por trás de um objeto selecionado que é executado quando esse objeto é ativado.

 A tabela a seguir lista as interfaces primárias usadas pela janela **Propriedades.**

|Nome da Interface|Descrição|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornece uma lista de categorias para a janela **Propriedades** e mapeia cada propriedade para uma categoria.|
|[IDispatch Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expõe os métodos e propriedades de um objeto a ferramentas de programação e outros aplicativos que suportam automação.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornece botões ellipsis (...) chamados *construtores* que abrem janelas de diálogo modal implementadas pelo próprio objeto. Usado quando um valor não é facilmente digitado pelo usuário em um campo de texto. Por exemplo, ele pode ser usado para abrir um seletor de cores que determina o valor RGB para você.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornece acesso a objetos usados para atualizar as informações exibidas na janela **Propriedades.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>é implementado por VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a serem exibidas.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornece informações sobre o tipo de objeto, como métodos de uma interface e campos de uma estrutura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Habilita que o VSPackages receba notificação de eventos de seleção e recupere informações sobre a hierarquia atual do projeto, item, valor do elemento e contexto de interface do comando.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornece ao ambiente acesso a várias seleções.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usado para fornecer nomes localizados em algumas propriedades exibidas na janela **Propriedades.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica VSPacotes registrados de alterações na seleção atual, valor do elemento ou contexto de interface do usuário de comando.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica o ambiente de uma alteração na seleção atual e fornece acesso a informações de hierarquia e itens relacionados à nova seleção.|

 Para obter `IDispatch`mais informações sobre, consulte a biblioteca MSDN.

## <a name="see-also"></a>Confira também
- [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
- [Interfaces e campos da janela Propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
