---
title: '&lt;&gt;Elemento Signature (implantação do ClickOnce) | Microsoft Docs'
description: O elemento Signature contém as informações necessárias para assinar digitalmente este manifesto de implantação. A assinatura de um manifesto de implantação é opcional, mas recomendada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d95398285d9106719f3c2444d54202b81cfee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877493"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;Elemento Signature (implantação do ClickOnce)
Contém as informações necessárias para assinar digitalmente este manifesto de implantação.

## <a name="syntax"></a>Sintaxe

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Comentários
 Assinar um manifesto de implantação usando uma assinatura de envelope é opcional, mas recomendado. Para obter mais informações sobre como assinar arquivos XML, consulte a recomendação World Wide Web Consortium, "sintaxe e processamento da assinatura XML", descrita em [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Se você quiser assinar seu manifesto, os hashes deverão ser fornecidos para todos os arquivos. Um manifesto com arquivos que não têm hash não pode ser assinado, pois os usuários não podem verificar o conteúdo de arquivos sem hash.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `Signature` elemento em um manifesto de implantação usado em uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
