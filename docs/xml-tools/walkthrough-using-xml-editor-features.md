---
title: 'Passo a passo: Usando recursos do editor de XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f0b4069bf1b74c15f9fcf7cdb7e488247b8548e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808485"
---
# <a name="walkthrough-use-xml-editor-features"></a>Passo a passo: Usar recursos do editor XML

As etapas nessa explicação passo a passo mostram como criar um novo documento XML. O passo a passo também usa alguns dos recursos do editor de XML que tornam valioso para a criação de XML.

> [!NOTE]
> Antes de iniciar o passo a passo, salve o *HireDate* arquivo (incluído abaixo neste tópico) para seu computador local.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para criar um novo arquivo XML e associá-lo a um esquema XML

1. Sobre o **arquivo** , aponte para **New**e clique em **arquivo**.

2. Selecione **arquivo XML** na **modelos** painel e clique em **abrir**.

     Um novo arquivo é aberto no editor. O arquivo contém uma declaração XML padrão, `<?xml version="1.0" encoding="utf-8">`.

3. Na janela de propriedades do documento, clique no botão Procurar (**...** ) sobre o **esquemas** campo.

     O **esquemas XSD** caixa de diálogo é exibida.

4. Clique em **Adicionar**.

     O **abrir esquema XSD** caixa de diálogo é exibida.

5. Selecione o *HireDate* do arquivo e clique em **abrir**.

6. Clique em **OK**.

     O esquema XML agora está associado com o documento XML. O esquema XML é usado para validar o documento. Também é usado pelo IntelliSense para preencher a lista de membros de elementos válidos.

## <a name="to-add-data"></a>Para adicionar dados

1. Tipo `<` no painel do editor.

     A lista de membros exibe os itens possíveis:

    - **! –** para adicionar um comentário.

    - **! DOCTYPE** para adicionar um tipo de documento.

    - **?** Para adicionar uma instrução de processamento.

    - **funcionário** para adicionar o elemento raiz.

2. Selecione **<!-** para adicionar um nó de comentário e pressione **Enter**.

     O editor insere uma marca de fim do comentário e colocar o cursor entre o início e marcas de comentário final.

3. Digite **arquivo de teste XML**.

4. Em uma nova linha, digite `<`e selecione **funcionário** da lista de membros.

     O editor adiciona o início de um elemento XML, `<employee`. Neste momento você pode adicionar atributos para o elemento ou você pode fechar a tag de início digitando `>`.

5. Tipo `>` para a marca de fechamento.

6. O editor adiciona a marca de fim. A marca de fim é adicionada com um a linha subescrita ondulada que indica um erro de validação. O **dica de ferramenta** exibe a mensagem: **O elemento "empregado" tem conteúdo incompleto. Esperado 'ID'**.

7. Tipo de `<` e selecione **ID** da lista de membros. Digite `>`.

     O editor adicione o elemento XML, `<ID></ID>`, e posicionar o cursor após a marca de início de identificação.

8. Tipo de **abc**.

     O **abc** texto tem uma linha ondulada. O **dica de ferramenta** exibe a mensagem: **O elemento 'ID' tem um valor inválido de acordo com seu tipo de dados**.

9. Clique com botão direito no elemento de identificação e selecione **ir para definição**.

     O editor abre o *HireDate* arquivo em uma nova janela de documento e posicionar o cursor na definição de elemento de esquema de ID.

10. Retornar para o arquivo XML e substitua os **abc** texto com **123**.

     A linha ondulada e **dica de ferramenta** são desmarcados no valor do elemento ID. O **dica de ferramenta** para o final do funcionário marca agora exibe a mensagem: **O elemento "empregado" tem conteúdo incompleto. Esperado 'Data de admissão'**.

11. Coloque o cursor após a marca de fim de ID, digite `<`, selecione **data de admissão** na lista de membro e, em seguida, digite `>`.

     O editor adicione o elemento XML, `<hire-date></hire-date>`, e posicionar o cursor após a marca de início da data de admissão.

12. Digite **2003-01-10** para o valor de data de admissão.

## <a name="to-format-the-xml-document"></a>Para formatar o documento XML

- Selecione o **Formatar documento** botão na barra de ferramentas do editor XML, ou pressione **Ctrl**+**eletrônico**,**1!d**.

   ![Botão de documento do formato XML no Visual Studio](media/format-xml-document.png)

   O documento XML é reformatado.

## <a name="to-save-the-xml-document"></a>Para salvar o documento XML

1. Dos **arquivo** menu, selecione **Salvar como**.

     O **salvar arquivo como** caixa de diálogo é exibida. O nome de arquivo padrão é *"XMLFile1"*.

2. Insira o nome do arquivo e o local para o documento XML e clique em **salvar**.

## <a name="hiredatexsd-file"></a>hireDate.xsd file

O arquivo de esquema a seguir é usado neste passo a passo:

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)