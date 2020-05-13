---
title: Campos e interfaces de janelas de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706156"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces e campos da janela Propriedades
O modelo de seleção para determinar quais informações são exibidas na janela **Propriedades** é baseado na janela que tem foco no IDE. Cada janela, e objeto dentro da janela selecionada, pode ter seu objeto de contexto de seleção empurrado para o contexto global de seleção. O ambiente atualiza o contexto de seleção global com valores de um quadro de janela quando essa janela tem o foco. Quando o foco muda, o contexto de seleção também muda.

## <a name="tracking-selection-in-the-ide"></a>Seleção de rastreamento no IDE
 A moldura da janela ou site, de propriedade <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>do IDE, tem um serviço chamado . As etapas a seguir mostram como uma alteração em uma seleção, causada pelo usuário alterando o foco para outra janela aberta ou selecionando um item de projeto diferente no **Solution Explorer,** é implementada para alterar o conteúdo exibido na janela **Propriedades.**

1. O objeto criado pelo seu VSPackage que está <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> situado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>nas chamadas de janela selecionadas para invocar .

2. O recipiente de seleção, fornecido pela <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> janela selecionada, cria seu próprio objeto. Quando a seleção é <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> alterada, o VSPackage é chamada para notificar quaisquer ouvintes no ambiente, incluindo a janela **Propriedades,** da alteração. Também fornece acesso a informações de hierarquia e itens relacionados à nova seleção.

3. Chamando-o <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passando-os os `VSHPROPID_BrowseObject` itens de hierarquia <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> selecionados no parâmetro povoa o objeto.

4. Um objeto derivado da [Interface IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) é devolvido para [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) para o item solicitado, e o <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ambiente o envolve em um (veja a etapa a seguir). Se a chamada falhar, o ambiente `IVsHierarchy::GetProperty`faz uma segunda chamada para , passando-a o recipiente de seleção [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que o item de hierarquia ou itens forneçam.

    O projeto VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> não cria porque a janela VSPackage fornecida pelo ambiente que <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> o implementa (por exemplo, **Solution Explorer)** constrói em seu nome.

5. O ambiente invoca os <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> métodos de obter `IDispatch` os objetos baseados na interface para preencher a janela **Propriedades.**

   Quando um valor na janela **Propriedades** é `IVsTrackSelectionEx::OnElementValueChangeEx` alterado, os VSPackages implementam e `IVsTrackSelectionEx::OnSelectionChangeEx` reportam a alteração ao valor do elemento. O ambiente então <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> invoca ou para manter as informações exibidas na janela **Propriedades** sincronizadas com os valores da propriedade. Para obter mais informações, consulte [Atualizar valores de propriedade na janela Propriedades](#updating-property-values-in-the-properties-window).

   Além de selecionar um item de projeto diferente no **Solution Explorer** para exibir propriedades relacionadas a esse item, você também pode escolher um objeto diferente dentro de um formulário ou janela de documento usando a lista de queda disponível na janela **Propriedades.** Para obter mais informações, consulte ['Lista de objetos da janela de propriedades'.](../../extensibility/internals/properties-window-object-list.md)

   Você pode alterar a forma como as informações são exibidas na grade da janela **Propriedades** de alfabética para categórica e, se disponível, você também pode abrir uma página de propriedade para um objeto selecionado clicando nos botões apropriados na janela **Propriedades.** Para obter mais informações, consulte [Botões de janela de propriedades](../../extensibility/internals/properties-window-buttons.md) e páginas de [propriedade](../../extensibility/internals/property-pages.md).

   Finalmente, a parte inferior da janela **Propriedades** também contém uma descrição do campo selecionado na grade da janela **Propriedades.** Para obter mais informações, consulte [Obter descrições de campo na janela Propriedades](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Atualizando valores de propriedade na janela propriedades
Existem duas maneiras de manter a janela **Propriedades** em sincronia com as alterações de valor da propriedade. A primeira é <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> chamar a interface, que fornece acesso à funcionalidade básica de janelas, incluindo acesso e criação de janelas de ferramentas e documentos fornecidas pelo ambiente. As etapas a seguir descrevem esse processo de sincronização.

### <a name="updating-property-values-using-ivsuishell"></a>Atualizando os valores de propriedade usando iVsuishell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para atualizar os valores de propriedade usando a interface IVsUIShell

1. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (através do serviço) sempre <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> que o VSPackages, projetos ou editores precisarem criar ou enumerar janelas de ferramentas ou documentos.

2. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para manter a janela **Propriedades** em sincronia com alterações de propriedade para <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> um <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> projeto (ou qualquer outro objeto selecionado sendo navegado pela janela **Propriedades)** sem implementar e disparar eventos.

3. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> os <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> métodos e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> estabelecer e desativar, respectivamente, a notificação do cliente <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>de eventos hierárquicos sem exigir a hierarquia para implementar .

### <a name="updating-property-values-using-iconnection"></a>Atualizando os valores de propriedade usando a iConexão
 A segunda maneira de manter a janela **Propriedades** em `IConnection` sincronia com as alterações de valor da propriedade é implementar no objeto conectável para indicar a existência das interfaces de saída. Se você deseja localizar o nome da <xref:System.ComponentModel.ICustomTypeDescriptor>propriedade, obtenha seu objeto de . A <xref:System.ComponentModel.ICustomTypeDescriptor> implementação pode modificar os descritores de propriedade que retorna e alterar o nome de uma propriedade. Para localizar a descrição, crie um <xref:System.ComponentModel.DescriptionAttribute> atributo que deriva e anule a propriedade Descrição.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerações na implementação da interface IConnection

1. `IConnection`fornece acesso a um subobjeto enumerador com a <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Ele também fornece acesso a todos os subobjetos do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> ponto de conexão, cada um dos quais implementa a interface.

2. Qualquer objeto de navegação é <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> responsável pela implementação de um evento. A janela **Propriedades** avisará para `IConnection`o evento definido através de .

3. Um ponto de conexão controla quantas conexões (uma <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>ou mais) permite na sua implementação de . Um ponto de conexão que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> permite <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> apenas uma interface pode retornar a partir do método.

4. Um cliente pode `IConnection` ligar para a interface para obter acesso <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> a um subobjeto enumerador com a interface. A <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface pode então ser chamada para enumerar pontos de conexão para cada ID (IDD) de interface de saída.

5. `IConnection`também pode ser chamado para obter acesso a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> subobjetos de ponto de conexão com a interface para cada IID de saída. Através <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> da interface, um cliente inicia ou encerra um loop consultivo com o objeto conectável e a sincronização do próprio cliente. O cliente também <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pode chamar a interface para obter <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> um objeto enumerador com a interface para enumerar as conexões que ele conhece.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Obtendo descrições de campo da janela propriedades
Na parte inferior da janela **Propriedades,** uma área de descrição exibe informações relacionadas ao campo de propriedade selecionado. Este recurso permanece ligado por padrão. Se você quiser ocultar o campo de descrição, clique com o botão direito do mouse na janela **Propriedades** e clique em **Descrição**. Ao fazer isso, também remove a marca de seleção ao lado do título **Descrição** na janela do menu. Você pode exibir o campo novamente seguindo os mesmos passos para alternar **a descrição** novamente.

 As informações no campo <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>de descrição vêm de . Cada método, interface, coclasse e assim por diante `helpstring` podem ter um atributo não localizado na biblioteca do tipo. A janela **Propriedades** recupera <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>a seqüência de .

### <a name="to-specify-localized-help-strings"></a>Para especificar strings de ajuda localizadas

1. Adicione `helpstringdll` o atributo à declaração`typelib`da biblioteca na biblioteca do tipo ().

   > [!NOTE]
   > Esta etapa é opcional se a biblioteca do tipo estiver em um arquivo da biblioteca de objetos (.olb).

2. Especifique `helpstringcontext` atributos para as strings. Você também `helpstring` pode especificar atributos.

    Esses atributos são `helpfile` `helpcontext` distintos dos atributos, que estão contidos em tópicos reais de ajuda de arquivo .chm.

   Para recuperar as informações de descrição a serem **Properties** exibidas <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> para o nome da propriedade destacada, a janela Propriedades solicita a propriedade selecionada, especificando o atributo desejado `lcid` para a seqüência de saída. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> encontra o arquivo .dll `helpstringdll` especificado `DLLGetDocumentation` no atributo e solicita esse `lcid` arquivo .dll com o contexto e atributo especificados.

   A assinatura e `DLLGetDocumentation` implementação são:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 A `DLLGetDocumentation` função deve ser uma exportação definida no arquivo .def para o DLL.

 Internamente, um arquivo .olb é criado que é na verdade um DLL. Esta DLL contém um recurso, o arquivo type library (.tlb) e uma função exportada, `DLLGetDocumentation`.

 No caso de arquivos .olb, o atributo `helpstringdll` é opcional porque é o mesmo arquivo que contém o próprio arquivo .tlb.

 Para obter strings para aparecer no painel **Descrições,** portanto, o mínimo `helpstring` que você tem que fazer é especificar o atributo na biblioteca do tipo. Se você quiser que essas strings sejam localizadas, você tem que especificar o atributo `helpstringdll` (opcional) e o atributo `helpstringcontext` (necessário) e implementar `DLLGetDocumentation`.

 Não há interfaces adicionais que precisam ser implementadas ao obter `helpstringcontext` informações `DLLGetDocumentation`localizadas através do atributo idl e .

 Outra forma de obter o nome localizado e a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>descrição de um imóvel é implementando . Para obter mais informações relacionadas à implementação deste método, consulte [Campos de janelas de propriedades e interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Confira também

- [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
