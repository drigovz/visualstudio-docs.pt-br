---
title: 'CA1063: Implementar IDisposable corretamente'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 22ecfcdd6dc20f5837622ec2cc3469f11c7efa8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788549"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementar IDisposable corretamente

|||
|-|-|
|NomeDoTipo|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

O <xref:System.IDisposable?displayProperty=nameWithType> interface não está implementado corretamente. Possíveis motivos para isso:

- <xref:System.IDisposable> é reimplantado na classe.

- Finalizar é reoverridden.

- Dispose () é substituído.

- O método Dispose () não é público, [lacrado](/dotnet/csharp/language-reference/keywords/sealed), ou nomeados **Dispose**.

- Dispose (bool) não é protegido, virtual ou sem lacre.

- Tipos sem lacre, Dispose () deve chamar Dispose (True).

- Para tipos sem lacre, a implementação de Finalize não chamar Dispose (bool) de um ou ambos os ou o finalizador da classe base.

Aviso CA1063 dispara a violação de qualquer um desses padrões.

Cada tipo sem lacre que declara e implementa o <xref:System.IDisposable> interface deve fornecer seu próprio `protected virtual void Dispose(bool)` método. `Dispose()` deve chamar `Dipose(true)`, e o finalizador deve chamar `Dispose(false)`. Se você criar um tipo sem lacre que declara e implementa o <xref:System.IDisposable> interface, você deve definir `Dispose(bool)` e chamá-lo. Para obter mais informações, consulte [limpar recursos não gerenciados (guia do .NET)](/dotnet/standard/garbage-collection/unmanaged) e [padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern).

Por padrão, essa regra olha apenas tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Todos os <xref:System.IDisposable> os tipos devem implementar a [padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern) corretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Examine seu código e determinar qual das seguintes resoluções corrigirá essa violação:

- Remover <xref:System.IDisposable> da lista de interfaces que são implementadas pelo seu tipo e substituir a implementação de Dispose da classe base em vez disso.

- Remova o finalizador do seu tipo, substitua Dispose (bool disposing) e coloque a lógica de finalização no caminho do código onde "disposing" é false.

- Substitua Dispose (bool disposing) e coloque a lógica de descarte no caminho do código onde "disposing" é true.

- Certifique-se de que Dispose () é declarado como público e [lacrado](/dotnet/csharp/language-reference/keywords/sealed).

- Renomear seu método dispose **Dispose** e certifique-se de que ele é declarado como público e [lacrado](/dotnet/csharp/language-reference/keywords/sealed).

- Certifique-se de que Dispose (bool) é declarado como protegido, virtual e sem lacre.

- Modificar Dispose () para que ele chame Dispose (True), em seguida, chama <xref:System.GC.SuppressFinalize%2A> na instância do objeto atual (`this`, ou `Me` no Visual Basic) e, em seguida, retorna.

- Modifique seu finalizador para que ele chama Dispose (False) e, em seguida, retorna.

- Se você criar um tipo sem lacre que declara e implementa o <xref:System.IDisposable> interface, certifique-se de que a implementação de <xref:System.IDisposable> segue o padrão descrito anteriormente nesta seção.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca1063.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Exemplo de pseudocódigo

O pseudocódigo a seguir fornece um exemplo geral de como Dispose (bool) devem ser implementadas em uma classe que usa gerenciada e recursos nativos.

```csharp
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
    // own unmanaged resources, but leave the other methods
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

## <a name="see-also"></a>Consulte também

- [Padrão (diretrizes de design do framework) de descarte](/dotnet/standard/design-guidelines/dispose-pattern)
- [Limpar recursos não gerenciados (guia do .NET)](/dotnet/standard/garbage-collection/unmanaged)