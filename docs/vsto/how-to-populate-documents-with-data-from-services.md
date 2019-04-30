---
title: 'Como: Preencher documentos com dados de serviços'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6239bc351872dc7a945c3fbff8ad1ed13817c3ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967778"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Como: Preencher documentos com dados de serviços

Acesso a dados funciona da mesma maneira no nível de documento para o Microsoft Office, como faz em projetos do Windows Forms. Usar as mesmas ferramentas e código para trazer os dados para sua solução, e você pode até mesmo usar controles dos Windows Forms para exibir os dados. Além disso, você pode tirar proveito dos controles, chamados de controles de host, que são objetos nativos no Microsoft Office Excel e Microsoft Office Word que foram aprimorados com eventos e a funcionalidade de associação de dados. Para obter mais informações, consulte [hospedam itens e visão geral dos controles](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

O exemplo a seguir mostra como adicionar controles ligados a dados a documentos em tempo de design. Para obter um exemplo de como adicionar controles ligados a dados nos suplementos do VSTO em tempo de execução, consulte [passo a passo: Associar aos dados de um serviço em um projeto de suplemento do VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração em vídeo relacionada, consulte [como fazer: Interagir com os serviços web do Microsoft Excel? ](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Para popular um projeto de nível de documento com os dados de um serviço web

1. Abra o **fontes de dados** janela e criar uma fonte de dados de serviço para seu projeto. Para obter mais informações, consulte [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md).

2. Arraste a tabela ou o campo desejado a **fontes de dados** janela ao documento.

     Um controle é criado no documento, um <xref:System.Windows.Forms.BindingSource> é criado que está associado à classe de objeto em seu projeto e classes são geradas para o serviço.

3. Em seu código, crie uma instância da classe de serviço da web conectado na etapa 1.

4. Se houver propriedades que são necessárias para a comunicação com o serviço web, crie instâncias dessas propriedades.

5. Criar e enviar uma solicitação de dados usando os métodos expostos pelo serviço da Web e quaisquer instâncias de propriedade criado na etapa 4.

     Os métodos que você usa dependem do serviço web oferece.

6. Atribuir a resposta de dados do serviço da web para o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade do <xref:System.Windows.Forms.BindingSource>.

Quando você executa o projeto, os controles exibem o primeiro registro na fonte de dados. Você pode habilitar a rolagem pelos registros manipulando os eventos de moeda usando os objetos no <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Consulte também

- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)
- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Como: Preencher planilhas com dados de um banco de dados](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Como: Preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Como: Preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Como: Atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)