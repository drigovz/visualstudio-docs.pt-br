---
title: 'Como: selecionar os esquemas XML a serem usados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666515"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Como: Selecione os esquemas XML para usar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML fornece um cache de esquema %InstallDir% localizado no diretório \ \ esquemas XML. O cache de esquema inclui esquemas XML conhecidos que são usados para validação do IntelliSense e de documento XML.

 A propriedade de documento **esquemas** é usada para selecionar um ou mais esquemas XSD (XML Schema Definition Language) a serem usados. Permite que você selecionar esquemas de cache do esquema, ou especifica um esquema que não está localizado no cache.

 Os esquemas que você especifica são salvos no arquivo oculto opções de usuário de solução (.sln), junto com quaisquer propriedades restantes de documento XML. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.

> [!NOTE]
> O editor pode validar usando um esquema embutido, ou um esquema referenciado pelo atributo de `xsd:schemaLocation` . Para obter mais informações, consulte [validação de documento XML](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para selecionar um esquema XML de cache do esquema

1. Abrir um arquivo no editor XML.

2. Na janela Propriedades do documento, clique no botão no campo **esquemas** .

    A caixa de diálogo **esquemas XML** é exibida. A caixa de diálogo lista todos os esquemas com uma extensão. xsd no cache de esquema (incluindo esquemas referenciados no arquivo catalog. xml) e também qualquer esquema que esteja na solução atual, aberto no Visual Studio, referenciado em um atributo `xsd:schemaLocation` ou referenciado no Propriedade **schemas** .

3. Selecione os esquemas para usar a validação seguindo um destes procedimentos:

   - Selecione um esquema listado na caixa de diálogo **esquemas XML** , clique na coluna **usar** e, em seguida, selecione **usar este esquema**.

     \- ou -

   - Selecione vários esquemas listados na caixa de diálogo **esquemas XML** , clique com o botão direito do mouse e selecione **usar este esquema**.

4. Clique em **OK**.

    A lista de esquemas selecionados é copiada de volta para a propriedade de documento **esquemas** .

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para adicionar um esquema XML para o cache de esquema

1. Na janela Propriedades do documento, clique no botão no campo **esquemas** .

2. Clique em **Adicionar**.

     Isso abre a caixa de diálogo **abrir esquema XSD** .

3. Procurar e selecione os esquemas para adicionar ao cache de esquema.

4. Clique em **Abrir**.

     Os esquemas foram adicionados ao cache de esquema e o valor de coluna de **uso** é definido para **usar esse esquema**.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para excluir um esquema XML de cache do esquema

1. Na janela Propriedades do documento, clique no botão no campo **esquemas** .

2. Selecione o esquema a ser removido e clique em **remover**.

     O esquema é removido do cache de memória do esquema, mas não é removido do sistema de arquivos.

    > [!NOTE]
    > Se você ainda tiver uma referência ao esquema por meio de um atributo `schemaLocation` ou se uma `targetNamespace` correspondente, a **remoção** não funcionará nessa situação devido à associação automática. Nesse caso, é recomendável que você marque o esquema como **não usar esquemas selecionados** na coluna **usar** .

## <a name="see-also"></a>Consulte também
 [Editor XML](../xml-tools/xml-editor.md) da [caixa de diálogo esquemas XML](../xml-tools/xml-schemas-dialog-box.md) do [cache de esquema](../xml-tools/schema-cache.md)
