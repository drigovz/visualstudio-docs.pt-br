---
title: Como criar marcadores de texto personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838284"
---
# <a name="how-to-create-custom-text-markers"></a>Como criar marcadores de texto personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você quiser criar um marcador de texto personalizado para enfatizar ou organizar o código, deverá executar as seguintes etapas:  
  
- Registrar o novo marcador de texto, para que outras ferramentas possam acessá-lo  
  
- Fornecer uma implementação e configuração padrão do marcador de texto  
  
- Criar um serviço que pode ser usado por outros processos para fazer uso do marcador de texto  
  
  Para obter detalhes sobre como aplicar um marcador de texto a uma região de código, consulte [como: usar marcadores de texto](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Para registrar um marcador personalizado  
  
1. Crie uma entrada de registro da seguinte maneira:  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>é `GUID` usado para identificar o marcador que está sendo adicionado  
  
    *\<Version>* é a versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , por exemplo, 8,0  
  
    *\<PackageGUID>* é o GUID do VSPackage que implementa o objeto Automation.  
  
   > [!NOTE]
   > O caminho raiz de HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* pode ser substituído por uma raiz alternativa quando o Shell do Visual Studio é inicializado, para obter mais informações, consulte [Opções de linha de comando](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Criar quatro valores em HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External marcadores\\*\<MarkerGUID>*  
  
   - (Padrão)  
  
   - Serviço  
  
   - DisplayName  
  
   - Pacote  
  
   - `Default` é uma entrada opcional do tipo REG_SZ. Quando definido, o valor da entrada é uma cadeia de caracteres que contém algumas informações de identificação úteis, por exemplo, "marcador de texto personalizado".  
  
   - `Service` é uma entrada do tipo REG_SZ que contém a cadeia de caracteres GUID do serviço que fornece o marcador de texto personalizado por Proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` é uma entrada do tipo REG_SZ que contém a ID de recurso do nome do marcador de texto personalizado. O formato é #YYYY.  
  
   - `Package` é a entrada do tipo REG_SZ que contém o `GUID` de VSPackage que fornece o serviço listado em serviço. O formato é {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Para criar um marcador de texto personalizado  
  
1. Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Sua implementação dessa interface define o comportamento e a aparência do seu tipo de marcador personalizado.  
  
     Essa interface é chamada quando  
  
    1. Um usuário inicia o IDE pela primeira vez.  
  
    2. Um usuário seleciona o **botão Redefinir padrões** na página de **Propriedades fontes e cores** na pasta **ambiente** , localizada no painel esquerdo da caixa de diálogo **Opções** , obtida no menu **ferramentas** do IDE.  
  
2. Implemente o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> método, especificando qual `IVsPackageDefinedTextMarkerType` implementação deve ser retornada com base no GUID do tipo de marcador especificado na chamada do método.  
  
     O ambiente chama esse método na primeira vez que o tipo de marcador personalizado é criado e especifica um GUID que identifica o tipo de marcador personalizado.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Para oferecer o tipo de marcador como um serviço  
  
1. Chame o <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> método para <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> é retornado.  
  
2. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> método, especificando o GUID que identifica o serviço de tipo de marcador personalizado e fornecendo um ponteiro para a implementação da <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface. Sua <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implementação deve retornar um ponteiro para a implementação da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interface.  
  
     Um cookie exclusivo que identifica que seu serviço é retornado. Posteriormente, você pode usar esse cookie para revogar o serviço de tipo de marcador personalizado chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> método da <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface que especifica esse valor de cookie.  
  
## <a name="see-also"></a>Consulte Também  
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como: implementar marcadores de erro](../extensibility/how-to-implement-error-markers.md)   
 [Como usar marcadores de texto](../extensibility/how-to-use-text-markers.md)
