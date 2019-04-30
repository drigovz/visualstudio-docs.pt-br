---
title: Usar arquivos de banco de dados local na visão geral das soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982245"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Usar arquivos de banco de dados local na visão geral das soluções do Office
  Você pode incluir um arquivo de banco de dados, como um SQL Server Express (*mdf*) arquivo ou o Microsoft Office Access (*. mdb*) arquivos em sua solução do Office. Isso permite que os usuários finais manter um banco de dados local em situações em que manter um banco de dados centralizado não é necessário, por exemplo, em uma solução local de inventário que é usada em apenas um único computador.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importar o arquivo de banco de dados em um projeto
 Para importar o arquivo de banco de dados para seu projeto, use o **Data Source Configuration Wizard** para criar uma fonte de dados com base no arquivo de banco de dados. O assistente adiciona o arquivo de banco de dados e um conjunto de dados tipado ao seu projeto.

## <a name="deploy-the-database-file"></a>Implantar o arquivo de banco de dados
 O **Data Source Configuration Wizard** usa um caminho relativo para criar conexões com o arquivo de banco de dados local. Isso permite que você copiar a solução de um computador para outro, se você mantiver as posições relativas dos arquivos.

 Se você implanta sua solução em um servidor e, em seguida, distribua o documento para cada usuário final, você deve distribuir o arquivo de banco de dados manualmente e instalá-lo na mesma posição em relação ao documento. Isso significa que o usuário final não é possível mover o documento para um novo local em seu computador, a menos que ele ou ela também move o arquivo de banco de dados.

## <a name="local-database-files-and-caching-the-dataset"></a>Arquivos de banco de dados local e o conjunto de dados de cache
 Em soluções de nível de documento para o Microsoft Office Excel e Microsoft Office Word, você pode armazenar em cache conjuntos de dados no documento, marcando a instância do conjunto de dados com o atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Quando você adiciona o arquivo de banco de dados ao seu projeto usando o **Data Source Configuration Wizard**, um conjunto de dados tipado é adicionado automaticamente ao seu projeto. Raramente é necessário aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> para esse conjunto de dados, porque os dados já são locais no computador do usuário. Para obter mais informações, consulte [armazenar em Cache dados](../vsto/caching-data.md).

## <a name="see-also"></a>Consulte também
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Como: Preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Como: Atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Dados de cache](../vsto/caching-data.md)
