---
title: 'CA1901: Declarações P-Invoke devem ser portáteis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed1385ee914fa8b0df31b360f4a1d8fdc8931332
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922411"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Declarações P/Invoke devem ser portáteis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Categoria|Microsoft.Portability|
|Alteração Significativa|Quebrando - se o valor de P/Invoke é visível fora do assembly. Não separável - se o valor de P/Invoke não é visível fora do assembly.|

## <a name="cause"></a>Causa
 Essa regra avalia o tamanho de cada parâmetro e o valor retornado de um P/Invoke e verifica se o seu tamanho, quando passa por marshaling para código não gerenciado em plataformas de 32 bits e 64 bits, está correto. A violação dessa regra mais comuns é passar um inteiro de tamanho fixo em que uma variável dependente de plataforma, tamanho de ponteiro é necessária.

## <a name="rule-description"></a>Descrição da Regra
 Qualquer um dos cenários a seguir viola essa regra ocorre:

-   O valor de retorno ou parâmetro é digitado como um inteiro de tamanho fixo quando ele deve ser digitado como um `IntPtr`.

-   O valor de retorno ou parâmetro é digitado como um `IntPtr` quando ele deve ser digitado como um inteiro de tamanho fixo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Você pode corrigir essa violação usando `IntPtr` ou `UIntPtr` para representar os identificadores em vez de `Int32` ou `UInt32`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você não deve suprimir esse aviso.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra uma violação dessa regra.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 Neste exemplo, o `nIconIndex` parâmetro é declarado como um `IntPtr`, que é de 4 bytes de largura em uma plataforma de 32 bits e 8 bytes de largura em uma plataforma de 64 bits. Na declaração não gerenciada que segue, você pode ver que `nIconIndex` é um inteiro sem sinal de 4 bytes em todas as plataformas.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Exemplo
 Para corrigir a violação, altere a declaração para o seguinte:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Consulte também
 [Avisos de portabilidade](../code-quality/portability-warnings.md)
