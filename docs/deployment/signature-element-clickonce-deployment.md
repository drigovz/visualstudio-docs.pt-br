---
title: '&lt;Assinatura&gt; elemento (implantação do ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c636a4178cf278c2bb0ad75f4e78b94758dda30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927481"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Assinatura&gt; elemento (implantação do ClickOnce)
Contém as informações necessárias para assinar digitalmente o manifesto de implantação.

## <a name="syntax"></a>Sintaxe

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Comentários
 Assinar um manifesto de implantação usando uma assinatura do envelope é opcional mas recomendado. Para obter mais informações sobre como assinar arquivos XML, consulte a World Wide Web Consortium recomendação, "Sintaxe e processamento de assinatura XML," descrita em [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).

 Se você desejar assinar seu manifesto, hashes devem ser fornecidos para todos os arquivos. Um manifesto com arquivos que não são transformadas em hash não pode ser assinado, porque os usuários não é possível verificar o conteúdo dos arquivos sem hash.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra uma `Signature` elemento em um manifesto de implantação usado em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.

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

## <a name="see-also"></a>Consulte também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)