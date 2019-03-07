---
title: Criar um esquema XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526123"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Como: Criar um esquema XML de um documento XML

O editor XML permite criar um esquema XSD (linguagem) de definição de esquema XML de um documento XML. O arquivo XML determina como o esquema é gerado da seguinte maneira:

- Se o documento XML não tiver nenhum esquema ou DTD (definição de tipo de documento) associado a ele, os dados no documento XML serão usados para inferir um novo esquema XML.

- Se o documento XML contiver um DTD associado, o DTD externo e o subconjunto interno serão convertidos em um esquema XML correspondente.

- Se o documento XML contiver dados internos com um esquema XDR reduzido de dados XML, o esquema XDR será convertido em um esquema XML correspondente.

Os esquemas que são criados, em seguida, são usados para fornecer o IntelliSense para o arquivo XML.

Para obter mais informações sobre o mecanismo de inferência de esquema, consulte [inferir um esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Para criar um esquema XML

1. Abra um arquivo XML no Visual Studio.

2. Na barra de menus, escolha **XML** > **Create Schema**.

   Um documento de esquema XML é criado e aberto para cada namespace encontrado no arquivo XML. Cada esquema é aberto como um arquivo variado temporário. Os esquemas podem ser salvos no disco, adicionados ao seu projeto ou descartados.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)