---
title: Usando assemblies de interoperabilidade do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722111"
---
# <a name="using-visual-studio-interop-assemblies"></a>Usando assemblies de interoperabilidade do Visual Studio
Os assemblies de interoperabilidade do Visual Studio permitem que os aplicativos gerenciados acessem as interfaces COM que fornecem extensibilidade do Visual Studio. Há algumas diferenças entre interfaces COM diretas e suas versões de interoperabilidade. Por exemplo, HRESULTs geralmente são representados como valores int e precisam ser manipulados da mesma maneira que as exceções, e os parâmetros (especialmente parâmetros de saída) são tratados de forma diferente.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Manipulando HRESULTs retornados ao código gerenciado de COM
 Quando você chama uma interface COM do código gerenciado, examina o valor HRESULT e lança uma exceção, se necessário. A classe <xref:Microsoft.VisualStudio.ErrorHandler> contém o método <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, que gera uma exceção COM, dependendo do valor do HRESULT passado para ele.

 Por padrão, o <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> gera uma exceção sempre que recebe um HRESULT que tem um valor menor que zero. Nos casos em que esses HRESULTs são valores aceitáveis e nenhuma exceção deve ser lançada, os valores de HRESULTs adicionais devem ser passados para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> depois que os valores são testados. Se o HRESULT que está sendo testado corresponder a qualquer valor de HRESULT explicitamente passado para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, nenhuma exceção será lançada.

> [!NOTE]
> A classe <xref:Microsoft.VisualStudio.VSConstants> contém constantes para HRESULTs comuns, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTs, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> também fornece os métodos <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, que correspondem às macros COM êxito e com falha no COM.

 Por exemplo, considere a seguinte chamada de função, na qual <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> é um valor de retorno aceitável, mas qualquer outro HRESULT menor que zero representa um erro.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Se houver mais de um valor de retorno aceitável, valores HRESULT adicionais só poderão ser acrescentados à lista na chamada para <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Retornando HRESULTs para COM do código gerenciado
 Se nenhuma exceção ocorrer, o código gerenciado retornará <xref:Microsoft.VisualStudio.VSConstants.S_OK> para a função COM que a chamou. A interoperabilidade COM dá suporte a exceções comuns que são fortemente tipadas em código gerenciado. Por exemplo, um método que recebe um argumento de `null` inaceitável gera um <xref:System.ArgumentNullException>.

 Se você não tiver certeza de qual exceção deve ser lançada, mas souber o HRESULT que deseja retornar ao COM, você poderá usar o método <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para lançar uma exceção apropriada. Isso funciona mesmo com um erro não padrão, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> tenta mapear o HRESULT passado para ele para uma exceção com rigidez de tipos. Se não puder, ele lançará uma exceção COM genérica em vez disso. O resultado final é que o HRESULT que você passa para <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do código gerenciado é retornado para a função COM que o chamou.

> [!NOTE]
> As exceções comprometem o desempenho e se destinam a indicar condições anormais do programa. As condições que ocorrem com frequência devem ser tratadas em linha, em vez de uma exceção gerada.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parâmetros IUnknown passados como tipo void * *
 Procure por [out] parâmetros que são definidos como tipo `void **` na interface COM, mas que são definidos como `[``iid_is``]` no protótipo do método de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Às vezes, uma interface COM gera um objeto `IUnknown` e a interface COM, em seguida, a transmite como tipo `void **`. Essas interfaces são especialmente importantes porque, se a variável for definida como [out] na IDL, o objeto `IUnknown` será contado com o método `AddRef`. Ocorrerá um vazamento de memória se o objeto não for manipulado corretamente.

> [!NOTE]
> Um objeto `IUnknown` criado pela interface COM e retornado em uma variável [out] causa um vazamento de memória se ele não for liberado explicitamente.

 Os métodos gerenciados que manipulam esses objetos devem tratar <xref:System.IntPtr> como um ponteiro para um objeto `IUnknown` e chamar o método <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> para obter o objeto. O chamador deve então converter o valor de retorno para qualquer tipo apropriado. Quando o objeto não for mais necessário, chame <xref:System.Runtime.InteropServices.Marshal.Release%2A> para liberá-lo.

 Veja a seguir um exemplo de como chamar o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> e manipular o objeto `IUnknown` corretamente:

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
> Os métodos a seguir são conhecidos por passar `IUnknown` ponteiros de objeto como tipo <xref:System.IntPtr>. Manipule-os conforme descrito nesta seção.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parâmetros opcionais [out]
 Procure parâmetros que são definidos como um tipo de dados [out] (`int`, `object` e assim por diante) na interface COM, mas que são definidos como matrizes do mesmo tipo de dados no protótipo do método de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Algumas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratam os parâmetros [out] como opcionais. Se um objeto não for necessário, essas interfaces COM retornarão um ponteiro `null` como o valor desse parâmetro em vez de criar o objeto [out]. Esse comportamento é esperado. Para essas interfaces, `null` ponteiros são assumidos como parte do comportamento correto do VSPackage e nenhum erro é retornado.

 Como o CLR não permite que o valor de um parâmetro [out] seja `null`, parte do comportamento projetado dessas interfaces não está diretamente disponível no código gerenciado. Os métodos do assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para interfaces afetadas configuram o problema definindo os parâmetros relevantes como matrizes, pois o CLR permite a passagem de matrizes de `null`.

 Implementações gerenciadas desses métodos devem colocar um `null` matriz no parâmetro quando não houver nada a ser retornado. Caso contrário, crie uma matriz de um elemento do tipo correto e coloque o valor de retorno na matriz.

 Os métodos gerenciados que recebem informações de interfaces com parâmetros opcionais [out] recebem o parâmetro como uma matriz. Basta examinar o valor do primeiro elemento da matriz. Se não for `null`, trate o primeiro elemento como se ele fosse o parâmetro original.

## <a name="passing-constants-in-pointer-parameters"></a>Passando constantes em parâmetros de ponteiro
 Procure parâmetros que são definidos como ponteiros [in] na interface COM, mas que são definidos como um tipo de <xref:System.IntPtr> no protótipo do método de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Um problema semelhante ocorre quando uma interface COM passa um valor especial, como 0,-1, ou-2, em vez de um ponteiro de objeto. Ao contrário de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], o CLR não permite que constantes sejam convertidas como objetos. Em vez disso, o assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] define o parâmetro como um tipo de <xref:System.IntPtr>.

 As implementações gerenciadas desses métodos devem aproveitar o fato de que a classe <xref:System.IntPtr> tem os construtores `int` e `void *` para criar um <xref:System.IntPtr> de um objeto ou de uma constante inteira, conforme apropriado.

 Os métodos gerenciados que recebem <xref:System.IntPtr> parâmetros desse tipo devem usar os operadores de conversão de tipo <xref:System.IntPtr> para lidar com os resultados. Primeiro, converta o <xref:System.IntPtr> para `int` e teste-o em relação a constantes inteiras relevantes. Se nenhum valor corresponder, converta-o em um objeto do tipo necessário e continue.

 Para obter exemplos disso, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>Valores de retorno OLE passados como parâmetros [out]
 Procure métodos que tenham um valor de retorno `retval` na interface COM, mas que tenham um valor de retorno de `int` e um parâmetro de matriz adicional [out] no protótipo do método de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Deve estar claro que esses métodos exigem tratamento especial porque os protótipos do método de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] têm mais um parâmetro do que os métodos da interface COM.

 Muitas interfaces COM que lidam com a atividade OLE enviam informações sobre o status de OLE de volta para o programa de chamada armazenado no `retval` valor de retorno da interface. Em vez de usar um valor de retorno, os métodos de assembly de interoperabilidade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] correspondentes enviam as informações de volta para o programa de chamada armazenado em um parâmetro de matriz [out].

 Implementações gerenciadas desses métodos devem criar uma matriz de elemento único do mesmo tipo que o parâmetro [out] e colocá-lo no parâmetro. O valor do elemento da matriz deve ser o mesmo que o `retval` COM apropriado.

 Os métodos gerenciados que chamam interfaces desse tipo devem efetuar pull do primeiro elemento da matriz [out]. Esse elemento pode ser tratado como se fosse um `retval` valor de retorno da interface COM correspondente.

## <a name="see-also"></a>Consulte também
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)