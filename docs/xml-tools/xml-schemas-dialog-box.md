---
title: esquemas XML
description: Saiba mais sobre a caixa de diálogo esquemas XML usada para selecionar quais esquemas XSD (linguagem de definição de esquema XML) associar a um documento XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c91e97d0508ab85893409386ddd3ab9dded7f45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874828"
---
# <a name="xml-schemas-dialog-box"></a>Caixa de diálogo de esquemas XML

A caixa de diálogo **esquemas XML** é usada para selecionar quais esquemas XSD (linguagem de definição de esquema XML) associar a um documento XML. Você pode selecionar um esquema de cache do esquema, ou especificar um esquema que não está localizado no cache. Os esquemas selecionados são considerados parte de um conjunto de esquema. O esquema é usado para o IntelliSense e também validação de documento XML.

Você pode acessar a caixa de diálogo **esquemas XML** clicando no botão **esquemas** na janela Propriedades do documento ou selecionando **esquemas** no menu **XML** .

## <a name="uielement-list"></a>Lista de elementos de interface do usuário

**Uso**

Selecione como o esquema XML deve ser usada.

- **Automático**. Este esquema não está em uso pelo documento atual mas está disponível para a associação automática. Se o documento XML declarar um namespace que corresponde `targetNamespace` deste esquema, o esquema será associado e é automaticamente encapsulado no conjunto de esquema.

- **Use este esquema**. Este esquema está sendo usado pelo documento atual. Qualquer o usuário que solicitou explicitamente este esquema está usado clicando nessa coluna, ou o esquema foi associado automaticamente com base em `targetNamespace`correspondente.

- Não **use esquemas selecionados**. Este esquema não é usado pelo documento atual, mesmo se o esquema tem `targetNamespace`correspondente. Essa configuração pode ser útil para resolver conflitos quando há mais de uma versão do mesmo esquema no cache ou na solução de esquema.

**Namespace de destino**

Exibe o namespace de destino associada com o esquema XML.

**Nome do Arquivo**

Exibe o nome do arquivo de esquema XML.

**Adicionar**

Abre a caixa de diálogo **abrir esquema XSD** , que permite que você selecione esquemas adicionais para adicionar ao conjunto de esquema. Quando você adiciona um esquema ao conjunto de esquema, o valor de coluna de **uso** é definido para **usar esse esquema**.

**Remover**

Remove o esquema do dataset selecionado de esquema. Remove o esquema de cache de memória do esquema, mas não no sistema de arquivos.

## <a name="see-also"></a>Confira também

- [Como: selecionar os esquemas XML a serem usados](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Cache de esquema](../xml-tools/schema-cache.md)
