---
title: 'Como: Criar um esquema XML de um documento XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32072a25a57988c0cf1273518e5c0a5d4745fe20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033798"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Como: Criar um esquema XML de um documento XML

O Editor de XML permite que você crie uma linguagem XSD (definição de esquema XML) de um documento XML. O documento de instância XML determina como o esquema é gerado da seguinte maneira:

-   Se o documento XML não tiver nenhum esquema ou DTD (definição de tipo de documento) associado a ele, os dados no documento XML serão usados para inferir um novo esquema XML.

-   Se o documento XML contiver um DTD associado, o DTD externo e o subconjunto interno serão convertidos em um esquema XML correspondente.

-   Se o documento XML contiver dados internos com um esquema XDR reduzido de dados XML, o esquema XDR será convertido em um esquema XML correspondente.

Os esquemas que são criados são, em seguida, usados para fornecer o IntelliSense para o documento XML.

Para obter mais informações sobre o mecanismo de inferência de esquema, consulte [inferindo um esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para criar um esquema XML

1.  Carregue um documento de instância XML no Editor de XML.

2.  Clique o **Create Schema** botão da **barra de ferramentas**.

     Um documento de esquema XML é criado e aberto para cada namespace encontrado no documento de instância XML. Cada esquema é aberto como um arquivo variado temporário.

     Os esquemas podem ser salvos no disco, adicionados ao seu projeto ou descartados.

    > [!NOTE]
    >  O **Create Schema** comando também está disponível no menu de atalho do Editor de XML e, nas **XML** menu.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)