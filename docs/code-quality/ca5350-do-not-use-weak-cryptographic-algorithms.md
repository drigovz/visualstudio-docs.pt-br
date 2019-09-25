---
title: 'CA5350: Não usar algoritmos de criptografia fracos'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aecd052e86a4c0366a1a43cb985ad50ab8862d8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236958"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Não usar algoritmos de criptografia fracos

|||
|-|-|
|NomeDoTipo|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Categoria|Microsoft.Cryptography|
|Alteração significativa|Sem interrupção|

> [!NOTE]
> Esse aviso foi atualizado pela última vez em 2015 de novembro.

## <a name="cause"></a>Causa

Os algoritmos de <xref:System.Security.Cryptography.TripleDES> criptografia, como e os algoritmos <xref:System.Security.Cryptography.RIPEMD160> de hash <xref:System.Security.Cryptography.SHA1> , como e são considerados fracos.

Esses algoritmos de criptografia não fornecem tanta garantia de segurança quanto as contrapartes mais modernas. Algoritmos <xref:System.Security.Cryptography.SHA1> de hash criptográfico <xref:System.Security.Cryptography.RIPEMD160> e fornecem menos resistência à colisão que os mais modernos algoritmos de hash. O algoritmo <xref:System.Security.Cryptography.TripleDES> de criptografia fornece menos bits de segurança do que mais algoritmos de criptografia modernos.

## <a name="rule-description"></a>Descrição da regra

Algoritmos de criptografia fracos e funções de hash são usados hoje por vários motivos, mas não devem ser usados para garantir a confidencialidade dos dados que eles protegem.

A regra é disparada quando encontra algoritmos 3DES, SHA1 ou RIPEMD160 no código e gera um aviso para o usuário.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Use opções criptograficamente mais fortes:

- Para criptografia TripleDES, use <xref:System.Security.Cryptography.Aes> criptografia.

- Para funções de hash SHA1 ou RIPEMD160, use aquelas na família [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) (por exemplo <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprimir um aviso dessa regra quando o nível de proteção necessário para os dados não exigir uma garantia de segurança.

## <a name="pseudo-code-examples"></a>Exemplos de pseudocódigo

No momento da redação deste artigo, o exemplo de pseudocódigo a seguir ilustra o padrão detectado por essa regra.

### <a name="sha-1-hashing-violation"></a>Violação de hash SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Solução:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>Violação de hash RIPEMD160

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Solução:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>Violação de criptografia TripleDES

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Solução:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```