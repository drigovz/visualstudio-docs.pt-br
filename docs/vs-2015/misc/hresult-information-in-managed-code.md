---
title: Informações de HRESULT em código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 4f80b575656c2d8b1740f217f2e144f89f254078
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681628"
---
# <a name="hresult-information-in-managed-code"></a>Informações de HRESULT em código gerenciado
A interação entre código gerenciado e COM pode causar problemas quando valores de retorno HRESULT são encontrados.  
  
 Em uma interface COM, um valor de retorno de HRESULT pode desempenhar essas funções:  
  
- Forneça informações sobre o erro (por exemplo, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> ).  
  
- Forneça informações de status sobre o comportamento normal do programa.  
  
  Quando chamadas COM em código gerenciado, HRESULTs podem causar esses problemas:  
  
- As funções COM que retornam valores HRESULT menores que zero (códigos de falha) geram exceções.  
  
- Os métodos COM que retornam regularmente dois ou mais códigos de êxito diferentes, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> ou <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , não podem ser diferenciados.  
  
  Como muitas das [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funções com retornam valores HRESULT menores que zero ou retornam códigos de êxito diferentes, os [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] assemblies de interoperabilidade foram gravados para que as assinaturas do método sejam preservadas. Todos os [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] métodos de interoperabilidade são do `int` tipo. Os valores HRESULT são passados pela camada de interoperabilidade sem alteração e sem gerar exceções.  
  
  Como uma função COM retorna um HRESULT para o método gerenciado que a chama, o método de chamada deve verificar o HRESULT e gerar exceções conforme necessário.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Manipulando HRESULTs retornados ao código gerenciado de COM  
 Quando você chama uma interface COM do código gerenciado, examina o valor HRESULT e lança uma exceção, se necessário. A <xref:Microsoft.VisualStudio.ErrorHandler> classe contém o <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> método, que gera uma exceção com, dependendo do valor do HRESULT passado para ele.  
  
 Por padrão, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> o gera uma exceção sempre que recebe um HRESULT que tem um valor menor que zero. Nos casos em que esses HRESULTs são valores aceitáveis e nenhuma exceção deve ser lançada, os valores de HRESULTs adicionais devem ser passados para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> depois que os valores são testados. Se o HRESULT que está sendo testado corresponder a qualquer valor de HRESULT explicitamente passado para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , nenhuma exceção será lançada.  
  
> [!NOTE]
> A <xref:Microsoft.VisualStudio.VSConstants> classe contém constantes para HRESULTs comuns, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULTs, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> também fornece os <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> métodos e, que correspondem às macros com êxito e com falha no com.  
  
 Por exemplo, considere a seguinte chamada de função, em que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> é um valor de retorno aceitável, mas qualquer outro HRESULT menor que zero representa um erro.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Se houver mais de um valor de retorno aceitável, valores HRESULT adicionais só poderão ser acrescentados à lista na chamada para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Retornando HRESULTs para COM do código gerenciado  
 Se nenhuma exceção ocorrer, o código gerenciado retornará <xref:Microsoft.VisualStudio.VSConstants.S_OK> à função com que a chamou. A interoperabilidade COM dá suporte a exceções comuns que são fortemente tipadas em código gerenciado. Por exemplo, um método que recebe um argumento inaceitável `null` lança um <xref:System.ArgumentNullException> .  
  
 Se você não tiver certeza de qual exceção deve ser lançada, mas souber o HRESULT que deseja retornar ao COM, você poderá usar o <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> método para gerar uma exceção apropriada. Isso funciona mesmo com um erro não padrão, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> tenta mapear o HRESULT passado a ele para uma exceção com rigidez de tipos. Se não puder, ele lançará uma exceção COM genérica em vez disso. O resultado final é que o HRESULT que você passa para <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do código gerenciado é retornado para a função com que o chamou.  
  
> [!NOTE]
> As exceções comprometem o desempenho e se destinam a indicar condições anormais do programa. As condições que ocorrem com frequência devem ser tratadas em linha, em vez de uma exceção gerada.  
  
## <a name="see-also"></a>Consulte Também  
 [VSPackages gerenciados](../misc/managed-vspackages.md)   
 [Interoperação com código não gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Como mapear HRESULTs e exceções](https://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Criando componentes COM para interoperação](https://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [VSPackages gerenciados](../misc/managed-vspackages.md)