---
title: Carregamento de documentos atrasado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708806"
---
# <a name="delayed-document-loading"></a>Carregamento de documento atrasado

Quando um usuário reabre uma solução do Visual Studio, a maioria dos documentos associados não são carregados imediatamente. O quadro da janela do documento é criado em um estado de inicialização pendente, e um documento de espaço reservado (chamado de quadro de stub) é colocado na tabela Documento em execução (RDT).

Sua extensão pode fazer com que os documentos do projeto sejam carregados desnecessariamente consultando elementos nos documentos antes de serem carregados, o que pode aumentar a pegada de memória geral do Visual Studio.

## <a name="document-loading"></a>Carregamento de documentos

O quadro de stub e o documento são totalmente inicializados quando o usuário acessa o documento, por exemplo, selecionando a guia do quadro da janela. O documento também pode ser inicializado por uma extensão que solicita os dados do documento, seja acessando o RDT diretamente para adquirir os dados do documento, ou acessando o RDT indiretamente fazendo uma das seguintes chamadas:

- O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> do quadro da janela.

- O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> de quadro de janela em qualquer uma das seguintes propriedades:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Se sua extensão usar código gerenciado, você não deve ligar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que tenha certeza de que o documento não está no estado de inicialização pendente ou que deseja que o documento seja totalmente inicializado. A razão é porque o método sempre retorna o objeto de dados doc, criando-o se necessário. Em vez disso, você deve chamar `IVsRunningDocumentTable4` um dos métodos na interface.

- Se sua extensão usar C++, você pode passar `null` para os parâmetros que você não deseja.

- Você pode evitar o carregamento desnecessário de documentos ligando para um dos seguintes métodos antes de solicitar as propriedades relevantes antes de solicitar outras propriedades:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>usando [__VSFPROPID6. VSFPROPID_PendingInitialization.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>)

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Este método <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> retorna um objeto que inclui um valor para [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) se o documento ainda não foi inicializado.

Você pode descobrir quando um documento foi carregado assinando o evento RDT que é levantado quando um documento é totalmente inicializado. Há duas possibilidades:

- Se o evento <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>afundar implementar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>você pode se inscrever,

- Caso contrário, você <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>pode se inscrever .

O exemplo a seguir é um cenário hipotético de acesso a documentos: uma extensão do Visual Studio quer exibir algumas informações sobre documentos abertos, por exemplo, a contagem de bloqueio de edição e algo sobre os dados do documento. Ele enumera os documentos no RDT usando, <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>em seguida, solicita <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> cada documento a fim de recuperar a contagem de bloqueio de edição e os dados do documento. Se o documento estiver no estado de inicialização pendente, a solicitação dos dados do documento faz com que ele seja desnecessariamente inicializado.

Uma maneira mais eficiente de acessar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> um documento é usar para <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> obter a contagem de bloqueio de edição e, em seguida, usar para determinar se o documento foi inicializado. Se as bandeiras não incluem [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), o documento já foi inicializado, e <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> solicitar os dados do documento com não causa qualquer inicialização desnecessária. Se as bandeiras incluírem [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), a prorrogação deve evitar solicitar os dados do documento até que o documento seja inicializado. Esta inicialização pode ser `OnAfterAttributeChange(Ex)` detectada no manipulador de eventos.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Teste extensões para ver se forçam a inicialização

Não há nenhuma sugestão visível para indicar se um documento foi inicializado, por isso pode ser difícil descobrir se sua extensão está forçando a inicialização. Você pode definir uma chave de registro que facilita a verificação, pois faz com que o título de cada documento que não esteja totalmente inicializado tenha o texto *[Stub]* no título.

Em **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, definir **StubTabTitleFormatString** para * {0} [Stub]*.
