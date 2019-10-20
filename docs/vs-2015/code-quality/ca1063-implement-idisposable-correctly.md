---
title: 'CA1063: implementar IDisposable corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fe2982ab9e1b3951583b268eadb44c97c8e4805
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663633"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: implementar IDisposable corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 o `IDisposable` não está implementado corretamente. Alguns motivos para esse problema estão listados aqui:

- IDisposable é implementado novamente na classe.

- Finalize é substituído novamente.

- Dispose é substituído.

- Dispose () não é Public, sealed ou named Dispose.

- Dispose (bool) não é protegido, virtual ou não lacrado.

- Em tipos sem lacre, Dispose () deve chamar Dispose (true).

- Para tipos sem lacre, a implementação Finalize não chama um ou ambos Dispose (bool) ou o finalizador de classe Case.

  A violação de qualquer um desses padrões irá disparar esse aviso.

  Cada tipo de raiz IDisposable sem lacre deve fornecer seu próprio método de descarte (booliano virtual void) protegido. Dispose () deve chamar Dispose (true) e Finalize deve chamar Dispose (false). Se você estiver criando um tipo de IDisposable raiz não lacrado, deverá definir Dispose (bool) e chamá-lo. Para obter mais informações, consulte [limpando recursos não gerenciados](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) na seção [diretrizes de design do Framework](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) da documentação do .NET Framework.

## <a name="rule-description"></a>Descrição da Regra
 Todos os tipos IDisposable devem implementar o padrão Dispose corretamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Examine seu código e determine quais das resoluções a seguir corrigirão essa violação.

- Remova IDisposable da lista de interfaces implementadas por {0} e substitua a implementação de descarte de classe base em vez disso.

- Remova o finalizador do tipo {0}, substitua Dispose (descarte de bool) e coloque a lógica de finalização no caminho do código onde ' disposição ' é false.

- Remova {0}, substitua Dispose (descarte de bool) e coloque a lógica de descarte no caminho de código onde ' disposição ' é true.

- Verifique se {0} está declarada como pública e lacrada.

- Renomeie {0} como ' Dispose ' e verifique se ele está declarado como público e lacrado.

- Verifique se {0} está declarada como protegida, virtual e sem lacre.

- Modifique {0} para que chame Dispose (true) e, em seguida, chame GC. SuppressFinalize na instância do objeto atual (' this ' ou ' me ' em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) e, em seguida, retorna.

- Modifique {0} para que chame Dispose (false) e, em seguida, retorne.

- Se você estiver escrevendo uma classe IDisposable raiz sem lacre, certifique-se de que a implementação de IDisposable segue o padrão descrito anteriormente nesta seção.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de pseudo-código
 O pseudocódigo a seguir fornece um exemplo geral de como Dispose (bool) deve ser implementado em uma classe que usa recursos gerenciados e nativos.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
