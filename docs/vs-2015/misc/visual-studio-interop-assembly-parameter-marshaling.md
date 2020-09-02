---
title: Marshaling de parâmetro de assembly de interoperabilidade do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686919"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Marshaling do parâmetro de assembly de interoperabilidade do Visual Studio
VSPackages que são escritos em código gerenciado podem precisar chamar ou ser chamados pelo código COM não gerenciado. Normalmente, os argumentos de método são transformados ou empacotados automaticamente pelo marshaler de interoperabilidade. No entanto, às vezes, os argumentos não podem ser transformados de maneira simples. Nesses casos, os parâmetros do protótipo do método de assembly de interoperabilidade são usados para corresponder os parâmetros da função COM o mais próximo possível. Para obter mais informações, consulte [Interop Marshaling](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Sugestões gerais  
  
##### <a name="read-the-reference-documentation"></a>Leia a documentação de referência  
 Uma maneira eficaz de detectar problemas de interoperabilidade é ler a documentação de referência para cada método.  
  
 A documentação de referência para cada método contém três seções relevantes:  
  
- O [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] protótipo de função com.  
  
- O protótipo do método de assembly de interoperabilidade.  
  
- Uma lista dos parâmetros COM e uma breve descrição de cada um.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Procure diferenças entre os dois protótipos  
 A maioria dos problemas de interoperabilidade derivam de incompatibilidades entre a definição de um tipo específico em uma interface COM e a definição do mesmo tipo nos [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assemblies de interoperabilidade. Por exemplo, considere a diferença na capacidade de passar um `null` valor em um parâmetro [out]. Você deve procurar diferenças entre os dois protótipos e considerar suas ramificações para os dados que estão sendo passados.  
  
##### <a name="read-the-parameter-definitions"></a>Ler as definições de parâmetro  
 Leia as definições de parâmetro. COM é menos estrito do que o Common Language Runtime (CLR) sobre a combinação de diferentes tipos de dados em um único parâmetro. As [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaces com tiram total proveito dessa flexibilidade. Qualquer parâmetro que possa passar ou exigir um valor ou tipo de dados não padrão, como um valor constante em um parâmetro de ponteiro, deve ser descrito como tal na documentação.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Objetos IUnknown passados como tipo void * *  
 Procure os parâmetros [out] que são definidos como tipo `void **` na interface com, mas que são definidos como `[``iid_is``]` no protótipo do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] método de assembly de interoperabilidade.  
  
 Às vezes, uma interface COM gera um `IUnknown` objeto e a interface com, em seguida, a transmite como tipo `void **` . Essas interfaces são especialmente importantes porque, se a variável for definida como [out] na IDL, o `IUnknown` objeto será contado com o `AddRef` método. Ocorrerá um vazamento de memória se o objeto não for manipulado corretamente.  
  
> [!NOTE]
> Um `IUnknown` objeto criado pela interface com e retornado em uma variável [out] causa um vazamento de memória se ele não for liberado explicitamente.  
  
 Os métodos gerenciados que manipulam esses objetos devem tratar <xref:System.IntPtr> como um ponteiro para um `IUnknown` objeto e chamar o <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obter o objeto. O chamador deve então converter o valor de retorno para qualquer tipo apropriado. Quando o objeto não for mais necessário, chame <xref:System.Runtime.InteropServices.Marshal.Release%2A> para liberá-lo.  
  
 Veja a seguir um exemplo de como chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> método e manipular o `IUnknown` objeto corretamente:  
  
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
> Os métodos a seguir são conhecidos por passar `IUnknown` ponteiros de objeto como tipo <xref:System.IntPtr> . Manipule-os conforme descrito nesta seção.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Parâmetros opcionais [out]  
 Procure parâmetros que são definidos como um tipo de dados [out] ( `int` , `object` , etc.) na interface com, mas que são definidos como matrizes do mesmo tipo de dados no protótipo do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] método de assembly de interoperabilidade.  
  
 Algumas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , tratam os parâmetros [out] como opcionais. Se um objeto não for necessário, essas interfaces COM retornarão um `null` ponteiro como o valor desse parâmetro em vez de criar o objeto [out]. Isso ocorre por design. Para essas interfaces, os `null` ponteiros são assumidos como parte do comportamento correto do VSPackage e nenhum erro é retornado.  
  
 Como o CLR não permite que o valor de um parâmetro [out] seja `null` , parte do comportamento projetado dessas interfaces não está diretamente disponível no código gerenciado. Os [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos de assembly de interoperabilidade para interfaces afetadas configuram o problema definindo os parâmetros relevantes como matrizes, pois o CLR permite a passagem de `null` matrizes.  
  
 Implementações gerenciadas desses métodos devem colocar uma `null` matriz no parâmetro quando não houver nada a ser retornado. Caso contrário, crie uma matriz de um elemento do tipo correto e coloque o valor de retorno na matriz.  
  
 Os métodos gerenciados que recebem informações de interfaces com parâmetros opcionais [out] recebem o parâmetro como uma matriz. Basta examinar o valor do primeiro elemento da matriz. Se não estiver `null` , trate o primeiro elemento como se ele fosse o parâmetro original.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Passando constantes em parâmetros de ponteiro  
 Procure parâmetros que são definidos como ponteiros [in] na interface COM, mas que são definidos como um <xref:System.IntPtr> tipo no protótipo do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] método de assembly de interoperabilidade.  
  
 Um problema semelhante ocorre quando uma interface COM passa um valor especial, como 0,-1, ou – 2, em vez de um ponteiro de objeto. Ao contrário [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] do, o CLR não permite que constantes sejam convertidas como objetos. Em vez disso, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly de interoperabilidade define o parâmetro como um <xref:System.IntPtr> tipo.  
  
 Implementações gerenciadas desses métodos devem aproveitar o fato de que a <xref:System.IntPtr> classe tem ambos `int` os `void *` construtores e para criar um <xref:System.IntPtr> de um objeto ou uma constante inteira, conforme apropriado.  
  
 Os métodos gerenciados que recebem <xref:System.IntPtr> parâmetros desse tipo devem usar os <xref:System.IntPtr> operadores de conversão de tipo para lidar com os resultados. Primeiro, converta o <xref:System.IntPtr> para `int` e teste-o em relação a constantes inteiras relevantes. Se nenhum valor corresponder, converta-o em um objeto do tipo necessário e continue.  
  
 Para obter exemplos disso, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Valores de retorno OLE passados como parâmetros [out]  
 Procure métodos que tenham um `retval` valor de retorno na interface com, mas que tenham um `int` valor de retorno e um parâmetro de matriz adicional [out] no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] protótipo do método de assembly de interoperabilidade. Deve estar claro que esses métodos exigem tratamento especial porque os [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] protótipos do método de assembly de interoperabilidade têm um parâmetro mais do que os métodos da interface com.  
  
 Muitas interfaces COM que lidam com a atividade OLE enviam informações sobre o status de OLE de volta para o programa de chamada armazenado no `retval` valor de retorno da interface. Em vez de usar um valor de retorno, os [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos de assembly de interoperabilidade correspondentes enviam as informações de volta para o programa de chamada armazenado em um parâmetro de matriz [out].  
  
 Implementações gerenciadas desses métodos devem criar uma matriz de elemento único do mesmo tipo que o parâmetro [out] e colocá-lo no parâmetro. O valor do elemento da matriz deve ser o mesmo que o COM apropriado `retval` .  
  
 Os métodos gerenciados que chamam interfaces desse tipo devem efetuar pull do primeiro elemento da matriz [out]. Esse elemento pode ser tratado como se fosse um `retval` valor de retorno da interface com correspondente.  
  
## <a name="see-also"></a>Consulte Também  
 [Marshaling de interoperabilidade](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshaling de interoperabilidade](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Solução de problemas de interoperabilidade](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackages gerenciados](../misc/managed-vspackages.md)