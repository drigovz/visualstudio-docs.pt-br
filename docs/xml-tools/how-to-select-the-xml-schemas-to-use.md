---
title: 'Como: Selecionar os esquemas XML que serão usados'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007382"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Como: Selecionar os esquemas XML que serão usados

O editor XML fornece um cache de esquema localizado na *%VSInstallDir%\xml\Schemas* directory. O cache de esquema inclui esquemas XML conhecidos que são usados para validação do IntelliSense e de documento XML.

Use o **esquemas** propriedade para selecionar um ou mais esquemas XSD (linguagem) de definição de esquema XML de documento. Você pode selecionar os esquemas do cache do esquema ou em outro lugar.

Os esquemas que você especifica são salvos em um arquivo de opções do usuário (oculto) solução (. *suo*), juntamente com todos os outros XML propriedades do documento. Como resultado, você não precisa digitar novamente esses valores na próxima vez que você abrir a solução.

> [!NOTE]
> O editor pode validar usando um esquema embutido ou um esquema referenciado pelo `xsd:schemaLocation` atributo. Para obter mais informações, consulte [validação de documento XML](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para selecionar um esquema XML de cache de esquema

1. Abrir um arquivo no editor XML.

2. Na janela de propriedades do documento, clique no **esquemas** campo. Quando o botão Procurar (...) for exibida, clique nele.

   ![Propriedade de esquemas para um arquivo XML](media/properties-schemas.png)

   O [caixa de diálogo de esquemas XML](xml-schemas-dialog-box.md) é aberta. A caixa de diálogo lista todos os esquemas com um. *xsd* extensão no cache de esquema (incluindo os Esquemas referenciados na *Catalog* arquivo) e também qualquer esquema que está na solução atual, aberta no Visual Studio, referenciada em um `xsd:schemaLocation` atributo ou referenciados na **esquemas** propriedade.

3. Selecione os esquemas para usar a validação seguindo um destes procedimentos:

   - Selecione um esquema listado na **esquemas XML** caixa de diálogo, clique o **uso** coluna e, em seguida, selecione **usar este esquema**.

     - ou -

   - Selecione vários esquemas listados na **esquemas XML** caixa de diálogo e, em seguida, o botão direito do mouse e selecione **usar este esquema**.

4. Escolha **OK**.

   A lista de esquemas selecionados será copiada para o **esquemas** propriedade de documento.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para adicionar um esquema XML para o cache de esquema

1. Na janela de propriedades do documento, clique no botão sobre a **esquemas** campo.

2. Clique em **Adicionar**.

   O **abrir esquema XSD** caixa de diálogo é aberta.

3. Procurar e selecione os esquemas para adicionar ao cache de esquema.

4. Clique em **Abrir**.

   Os esquemas são adicionados ao cache de esquema e o **uso** o valor da coluna é definido como **usar este esquema**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para excluir um esquema XML do cache de esquema

1. Na janela de propriedades do documento, clique no botão sobre a **esquemas** campo.

2. Selecione o esquema para remover e, em seguida, clique em **remover**.

   O esquema é removido do cache de memória do esquema, mas não é removido do sistema de arquivos.

   > [!NOTE]
   > Se você ainda terá uma referência para o esquema por meio de um `schemaLocation` atributo ou uma correspondência `targetNamespace` , em seguida, **remover** não funcionará nesta situação devido à associação automática. Nesse caso, é recomendável que você marca o esquema como **não use esquemas selecionados** na **usar** coluna.

## <a name="see-also"></a>Consulte também

- [Cache de esquema](../xml-tools/schema-cache.md)
- [Caixa de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)
- [Editor de XML](../xml-tools/xml-editor.md)