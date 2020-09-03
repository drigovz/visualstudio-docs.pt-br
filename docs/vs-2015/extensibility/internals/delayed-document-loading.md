---
title: Carregamento de documento atrasado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196865"
---
# <a name="delayed-document-loading"></a>Atraso no carregamento de documentos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando um usuário reabre uma solução do Visual Studio, a maioria dos documentos associados não é carregada imediatamente. O quadro da janela do documento é criado em um estado de inicialização pendente e um documento de espaço reservado (chamado de quadro de stub) é colocado na tabela de documentos em execução (RDT).  
  
 Sua extensão pode fazer com que os documentos do projeto sejam carregados desnecessariamente consultando elementos nos documentos antes de serem carregados. Isso pode aumentar a superfície geral da memória para o Visual Studio.  
  
## <a name="document-loading"></a>Carregamento de documentos  
 O quadro de stub e o documento são totalmente inicializados quando o usuário acessa o documento, por exemplo, selecionando a guia do quadro da janela. O documento também pode ser inicializado por uma extensão que solicita os dados do documento, acessando o RDT diretamente para adquirir os dados do documento ou acessando o RDT indiretamente, fazendo uma das seguintes chamadas:  
  
- O método de exibição de quadro de janela: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- O método GetProperty da moldura de janela <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> em qualquer uma das seguintes propriedades:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Se sua extensão usar código gerenciado, você não deverá chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a menos que esteja certo de que o documento não está no estado de inicialização pendente ou que você deseja que o documento seja totalmente inicializado. Isso ocorre porque esse método sempre retorna o objeto de dados Doc, criando-o se necessário. Em vez disso, você deve chamar um dos métodos na interface IVsRunningDocumentTable4.  
  
  Se sua extensão usar C++, você poderá passar `null` para os parâmetros que não deseja.  
  
  Você pode evitar o carregamento de documentos desnecessários chamando um dos métodos a seguir antes de solicitar as propriedades relevantes: antes de solicitar outras propriedades.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> usando o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Esse método retorna um <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objeto que inclui um valor para <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> se o documento ainda não tiver sido inicializado.  
  
  Você pode descobrir quando um documento foi carregado assinando o evento RDT que é gerado quando um documento é totalmente inicializado. Há duas possibilidades:  
  
- Se o coletor de eventos implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , você poderá assinar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- Caso contrário, você pode assinar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Veja a seguir um cenário de acesso a documentos hipotéticos. Uma extensão do Visual Studio deseja exibir algumas informações sobre documentos abertos, por exemplo, a contagem de bloqueios de edição e algo sobre os dados do documento. Ele enumera os documentos no RDT usando e, <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> em seguida, chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> para cada documento para recuperar os dados de documento e de contagem de bloqueios de edição. Se o documento estiver no estado de inicialização pendente, a solicitação dos dados do documento fará com que ele seja desnecessariamente inicializado.  
  
  Uma maneira mais eficiente de fazer isso é usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> para obter a contagem de bloqueios de edição e, em seguida, usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> para determinar se o documento foi inicializado. Se os sinalizadores não incluírem <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , o documento já foi inicializado e a solicitação dos dados do documento com o não <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> causará nenhuma inicialização desnecessária. Se os sinalizadores forem incluídos <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , a extensão deverá evitar solicitar os dados do documento até que o documento seja inicializado. Isso pode ser detectado no manipulador de eventos OnAfterAttributeChange (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testando extensões para ver se elas forçam a inicialização  
 Não há nenhuma indicação visível para indicar se um documento foi inicializado, portanto, pode ser difícil descobrir se a extensão está forçando a inicialização. Você pode definir uma chave do registro que facilita a verificação, porque ela faz com que o título de cada documento que não está totalmente inicializado tenha o texto `[Stub]` no título.  
  
 Em **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]**, defina **StubTabTitleFormatString** como ** {0} [stub]**.
