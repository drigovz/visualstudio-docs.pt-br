---
title: Obtendo descrições de campo na janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703975"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Obtendo descrições dos campos na janela Propriedades
Na parte inferior da janela **Propriedades** , uma área de descrição exibe informações relacionadas ao campo de propriedade selecionado. Este recurso permanece ligado por padrão. Se você quiser ocultar o campo Descrição, clique com o botão direito do mouse na janela **Propriedades** e clique em **Descrição**. Isso também remove a marca de seleção ao lado do título da **Descrição** na janela do menu. Você pode exibir o campo novamente seguindo as mesmas etapas para alternar a **Descrição** novamente.  
  
 As informações no campo Descrição vêm de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Cada método, interface, coclasse e assim por diante pode ter um atributo não local `helpstring` na biblioteca de tipos. A janela **Propriedades** recupera a cadeia de caracteres de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .  
  
### <a name="to-specify-localized-help-strings"></a>Para especificar cadeias de caracteres de ajuda localizadas  
  
1. Adicione o `helpstringdll` atributo à instrução da biblioteca na biblioteca de tipos ( `typelib` ).  
  
   > [!NOTE]
   > Esta etapa será opcional se a biblioteca de tipos estiver em um arquivo de biblioteca de objetos (. olb).  
  
2. Especifique `helpstringcontext` atributos para as cadeias de caracteres. Você também pode especificar `helpstring` atributos.  
  
    Esses atributos são distintos dos `helpfile` `helpcontext` atributos e, que estão contidos nos tópicos de ajuda de arquivo. chm reais.  
  
   Para recuperar as informações de descrição a serem exibidas para o nome da propriedade realçado, a janela **Propriedades** chama <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> a propriedade selecionada, especificando o `lcid` atributo desejado para a cadeia de caracteres de saída. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> localiza o arquivo. dll especificado no `helpstringdll` atributo e chama `DLLGetDocumentation` esse arquivo. dll com o contexto e o atributo especificados `lcid` .  
  
   A assinatura e a implementação do `DLLGetDocumentation` são:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 A `DLLGetDocumentation` função deve ser uma exportação definida no arquivo. def para a dll.  
  
 Internamente, um arquivo. olb é criado, o que é, na verdade, uma DLL. Essa DLL contém um recurso, o arquivo de biblioteca de tipos (. tlb) e uma função exportada, `DLLGetDocumentation` .  
  
 No caso de arquivos. olb, o `helpstringdll` atributo é opcional porque ele é o mesmo arquivo que contém o próprio arquivo. tlb.  
  
 Para que as cadeias de caracteres sejam exibidas no painel de **descrições** , portanto, o mínimo que você precisa fazer é especificar o `helpstring` atributo na biblioteca de tipos. Se desejar que essas cadeias de caracteres sejam localizadas, você precisará especificar o `helpstringdll` atributo (opcional) e o `helpstringcontext` atributo (obrigatório) e implementá-los `DLLGetDocumentation` .  
  
 Não há interfaces adicionais que precisam ser implementadas ao obter informações localizadas por meio do `helpstringcontext` atributo de IDL e `DLLGetDocumentation` .  
  
 Outra maneira de obter o nome localizado e a descrição de uma propriedade é implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Para obter mais informações relacionadas à implementação desse método, consulte [Propriedades e campos da janela de propriedade](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Campos e interfaces da janela de propriedades](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [identificação](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)