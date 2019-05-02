---
title: 'Como: Mapear esquemas para documentos do Word dentro do Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c6f9ee9a7b636c6c12bfe2f8debcc05911e3b04
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441762"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Como: Mapear esquemas para documentos do Word dentro do Visual Studio
  **Importante** as informações que propus neste tópico sobre o Microsoft Word são desenvolver ou apresentadas exclusivamente para o uso e benefício de indivíduos e organizações que estão localizados fora dos Estados Unidos e seus territórios ou que estão usando o programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removido uma implementação da funcionalidade específica relacionada para XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word não podem ser lidas ou usadas por indivíduos ou organizações nos Estados Unidos ou em seus territórios de quem estão usando ou desenvolver programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft depois de 10 de janeiro de 2010 ; Esses produtos não se comportará como produtos licenciados antes dessa data ou adquirido e licenciado para uso fora dos Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Você pode mapear um esquema XML para um documento enquanto o documento está aberto no Visual Studio. Você usa as mesmas ferramentas do Microsoft Office Word que você usa quando o documento é aberto fora do Visual Studio. O projeto do Office cria os objetos de mesmos se você mapear o esquema para o documento antes ou depois de criar sua solução do Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Para mapear um esquema XML para um documento do Word no Visual Studio

1. Abra o projeto de documento ou modelo do Word dentro do Visual Studio.

2. Clique para mover o foco para o designer do documento.

3. Na faixa de opções, clique no **desenvolvedor** guia.

    > [!NOTE]
    > Se o **desenvolvedor** guia não estiver visível, você deve primeiro Mostrar. Para obter mais informações, confira [Como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. No **XML** , clique em **esquema**.

     O **modelos e suplementos** caixa de diálogo é aberta.

5. Clique o **esquema XML** guia.

6. Clique em **adicionar esquema**.

     O **adicionar esquema** caixa de diálogo é aberta.

7. Navegue até o arquivo de esquema, selecione-o e, em seguida, clique em **aberto**.

     O **configurações de esquema** caixa de diálogo é aberta.

8. Atribuir um alias ou clique em **Okey** para adicionar o esquema sem um alias.

9. Clique em **OK**.

     O **estrutura XML** janela é aberta.

10. Arrastar os elementos do **estrutura XML** janela para os locais em seu documento onde você deseja que os controles correspondentes a serem criados.

## <a name="see-also"></a>Consulte também
- [Como: Mapear esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Esquemas e dados em personalizações no nível de documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
