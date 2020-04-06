---
title: Usando o Visual Studio Interop Assemblies | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704126"
---
# <a name="using-visual-studio-interop-assemblies"></a>Usando assemblies de interoperabilidade do Visual Studio
Os conjuntos interop do Visual Studio permitem que aplicativos gerenciados acessem as interfaces COM que fornecem extensibilidade do Visual Studio. Existem algumas diferenças entre interfaces COM retas e suas versões interop. Por exemplo, os HRESULTs são geralmente representados como valores int e precisam ser tratados da mesma forma que exceções, e os parâmetros (especialmente os parâmetros de saída) são tratados de forma diferente.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Manuseio de HRESULTs Retornados ao Código Gerenciado da COM
 Quando você chamar uma interface COM de código gerenciado, examine o valor HRESULT e lance uma exceção, se necessário. A <xref:Microsoft.VisualStudio.ErrorHandler> classe <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> contém o método, que lança uma exceção COM, dependendo do valor do HRESULT passado para ele.

 Por padrão, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> lança uma exceção sempre que é aprovada um HRESULT que tem um valor menor que zero. Nos casos em que tais HRESULTs são valores aceitáveis e nenhuma exceção <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> deve ser lançada, os valores de HRESULTS adicionais devem ser passados para depois que os valores forem testados. Se o HRESULT for testado corresponder a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>quaisquer valores De HRESULT explicitamente passados para , nenhuma exceção será lançada.

> [!NOTE]
> A <xref:Microsoft.VisualStudio.VSConstants> classe contém constantes para HRESULTS <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>comuns, por exemplo, e , e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>também fornece <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> os métodos, que correspondem às macros SUCCEEDED e FAILED no COM.

 Por exemplo, considere a seguinte <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> chamada de função, na qual é um valor de retorno aceitável, mas qualquer outro HRESULT menor que zero representa um erro.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Se houver mais de um valor de retorno aceitável, valores adicionais de <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>HRESULT podem ser anexados à lista na chamada para .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Retornando HRESULTS para COM a partir de código gerenciado
 Se não houver exceção, <xref:Microsoft.VisualStudio.VSConstants.S_OK> o código gerenciado retorna à função COM que o chamou. O COM interop suporta exceções comuns que são fortemente digitadas no código gerenciado. Por exemplo, um método que `null` recebe <xref:System.ArgumentNullException>um argumento inaceitável lança um .

 Se você não tiver certeza de qual exceção jogar, mas você sabe que <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> o HRESULT que deseja retornar ao COM, você pode usar o método para lançar uma exceção apropriada. Isso funciona mesmo com um erro <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>fora do padrão, por exemplo, . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>tentativas de mapear o HRESULT passou para ele para uma exceção fortemente digitada. Se não puder, ele lança uma exceção com genérica em vez disso. O resultado final é que o <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> HRESULT para o código gerenciado é devolvido à função COM que o chamou.

> [!NOTE]
> As exceções comprometem o desempenho e destinam-se a indicar condições anormais do programa. As condições que ocorrem muitas vezes devem ser tratadas inline, em vez de uma exceção lançada.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parâmetros iUnknown passados como tipo vazio**
 Procure por parâmetros [out] `void **` que são definidos como tipo `[``iid_is``]` na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface COM, mas que são definidos como no protótipo do método de montagem interop.

 Às vezes, uma `IUnknown` interface COM gera um objeto, `void **`e a interface COM passa-o como tipo . Essas interfaces são especialmente importantes porque se a variável é definida como `IUnknown` [out] no IDL, então o objeto é contado com referência com o `AddRef` método. Um vazamento de memória ocorre se o objeto não for manuseado corretamente.

> [!NOTE]
> Um `IUnknown` objeto criado pela interface COM e retornado em uma variável [out] causa um vazamento de memória se ele não for explicitamente liberado.

 Os métodos gerenciados que <xref:System.IntPtr> manuseiam tais `IUnknown` objetos devem <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> tratar como um ponteiro para um objeto e chamar o método para obter o objeto. O chamador deve, então, lançar o valor de retorno para qualquer tipo apropriado. Quando o objeto não for <xref:System.Runtime.InteropServices.Marshal.Release%2A> mais necessário, ligue para liberá-lo.

 A seguir está um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> exemplo de `IUnknown` chamar o método e manusear o objeto corretamente:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> Os seguintes métodos `IUnknown` são conhecidos <xref:System.IntPtr>por passar ponteiros de objeto como tipo . Manuseie-os como descrito nesta seção.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parâmetros opcionais [out]
 Procure parâmetros definidos como um tipo`int`de `object`dados [out] (, e assim por diante) na interface COM, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mas que são definidos como matrizes do mesmo tipo de dados no protótipo do método de montagem interop.

 Algumas interfaces COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>tais como , tratam os parâmetros [out] como opcionais. Se um objeto não for necessário, `null` essas interfaces COM retornarão um ponteiro como o valor desse parâmetro em vez de criar o objeto [out]. Isso ocorre por design. Para essas interfaces, `null` os ponteiros são assumidos como parte do comportamento correto do VSPackage, e nenhum erro é retornado.

 Como o CLR não permite que o valor de `null`um parâmetro [out] seja, parte do comportamento projetado dessas interfaces não está diretamente disponível dentro do código gerenciado. Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de montagem de interop para interfaces afetadas funcionam em torno do `null` problema definindo os parâmetros relevantes como arrays porque o CLR permite a passagem de arrays.

 Implementações gerenciadas desses métodos `null` devem colocar uma matriz no parâmetro quando não há nada a ser devolvido. Caso contrário, crie uma matriz de um elemento do tipo correto e coloque o valor de retorno na matriz.

 Métodos gerenciados que recebem informações de interfaces com parâmetros opcionais [out] recebem o parâmetro como uma matriz. Basta examinar o valor do primeiro elemento da matriz. Se não `null`for, trate o primeiro elemento como se fosse o parâmetro original.

## <a name="passing-constants-in-pointer-parameters"></a>Passando constantes nos parâmetros do ponteiro
 Procure por parâmetros definidos como [in] ponteiros na interface <xref:System.IntPtr> COM, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mas que são definidos como um tipo no protótipo do método de montagem interop.

 Um problema semelhante ocorre quando uma interface COM passa um valor especial, como 0, -1 ou -2, em vez de um ponteiro de objeto. Ao [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]contrário, a CLR não permite que as constantes sejam lançadas como objetos. Em vez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] disso, o conjunto interop <xref:System.IntPtr> define o parâmetro como um tipo.

 Implementações gerenciadas desses métodos devem aproveitar o <xref:System.IntPtr> fato `int` de `void *` que a classe <xref:System.IntPtr> tem tanto e construtores para criar um a partir de um objeto ou uma constante inteira, conforme apropriado.

 Métodos gerenciados <xref:System.IntPtr> que recebem parâmetros <xref:System.IntPtr> desse tipo devem usar os operadores de conversão de tipo para lidar com os resultados. Primeiro converta `int` o para e teste-o <xref:System.IntPtr> contra constantes inteiras relevantes. Se nenhum valor corresponder, converta-o em um objeto do tipo necessário e continue.

 Para exemplos disso, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> veja <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>e .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valores de retorno de OLE passados como parâmetros [out]
 Procure métodos que `retval` tenham um valor de retorno na `int` interface COM, mas que tenham um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valor de retorno e um parâmetro de matriz adicional [out] no protótipo do método de montagem interop. Deve ficar claro que esses métodos requerem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um manuseio especial porque os protótipos do método de montagem interop têm um parâmetro a mais do que os métodos de interface COM.

 Muitas interfaces COM que lidam com a atividade oLE enviam informações `retval` sobre o status OLE de volta ao programa de chamada armazenado no valor de retorno da interface. Em vez de usar um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valor de retorno, os métodos de montagem interop correspondentes enviam as informações de volta para o programa de chamada armazenado em um parâmetro de matriz [out].

 Implementações gerenciadas desses métodos devem criar uma matriz de elemento único do mesmo tipo que o parâmetro [out] e colocá-lo no parâmetro. O valor do elemento matriz deve ser `retval`o mesmo que o COM apropriado .

 Métodos gerenciados que chamam interfaces desse tipo devem puxar o primeiro elemento para fora da matriz [out]. Este elemento pode ser tratado `retval` como se fosse um valor de retorno da interface COM correspondente.

## <a name="see-also"></a>Confira também
- [Interoperação com Código Não Gerenciado](/dotnet/framework/interop/index)
