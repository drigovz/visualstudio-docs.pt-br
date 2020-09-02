---
title: 'Como: suprimir notificações de alteração de arquivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204075"
---
# <a name="how-to-suppress-file-change-notifications"></a>Como suprimir notificações de alteração de arquivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando o arquivo físico que representa o buffer de texto tiver sido alterado, uma caixa de diálogo será exibida com a mensagem deseja **salvar as alterações nos seguintes itens?** Isso é conhecido como notificação de alteração de arquivo. Se muitas alterações forem para o arquivo, no entanto, essa caixa de diálogo será exibida repetidamente e poderá ser irritante rapidamente.  
  
 Você pode suprimir programaticamente essa caixa de diálogo usando o procedimento a seguir. Ao fazer isso, você pode recarregar um arquivo imediatamente sem precisar solicitar que o usuário salve as alterações a cada vez.  
  
### <a name="to-suppress-file-change-notification"></a>Para suprimir a notificação de alteração de arquivo  
  
1. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> método para determinar qual objeto de buffer de texto está associado ao arquivo aberto.  
  
2. Direcione o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto que está na memória para ignorar o monitoramento de alterações de arquivo obtendo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> interface do <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto (dados do documento) e, em seguida, implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método com o `fIgnore` parâmetro definido como `true` .  
  
3. Chame os métodos nas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaces e para atualizar o objeto na memória <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> com as alterações de arquivo (por exemplo, quando um campo é adicionado ao seu componente).  
  
4. Atualize o arquivo em disco com as alterações sem considerar as edições pendentes que o usuário pode ter em andamento.  
  
     Dessa forma, quando você direciona o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para retomar o monitoramento de notificações de alteração de arquivo, o buffer de texto na memória reflete as alterações que você gerou, bem como todas as outras edições pendentes. O arquivo em disco reflete o código mais recente gerado por você e todas as alterações salvas anteriormente pelo usuário no código editado pelo usuário.  
  
5. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> método para notificar o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto para retomar o monitoramento de notificações de alteração de arquivo definindo o `fIgnore` parâmetro como `false` .  
  
6. Se você planeja fazer várias alterações no arquivo, como no caso do SCC (controle de código-fonte), você deve dizer ao serviço de alteração de arquivo global para suspender temporariamente as notificações de alteração de arquivo.  
  
     Por exemplo, se você reescrever o arquivo e, em seguida, alterar o carimbo de data/hora, deverá suspender as notificações de alteração de arquivo, pois as operações Rewrite e timestample cada contam como um evento de alteração de arquivo separado. Para habilitar a notificação de alteração de arquivo global, você deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> método.  
  
## <a name="example"></a>Exemplo  
 O seguinte demonstra como suprimir a notificação de alteração de arquivo.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se seu caso envolve várias alterações no arquivo, como no caso do SCC, é importante retomar as notificações de alteração de arquivo global antes de alertar os dados do documento para retomar o monitoramento das alterações de arquivo.
