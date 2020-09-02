---
title: Visão geral de usar arquivos de banco de dados local em soluções do Office
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982245"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Visão geral de usar arquivos de banco de dados local em soluções do Office
  Você pode incluir um arquivo de banco de dados, como um arquivo SQL Server Express (*. MDF*) ou um arquivo Microsoft Office Access (*. mdb*), em sua solução do Office. Isso permite que os usuários finais mantenham um banco de dados local em situações em que a manutenção de um banco de dados centralizado não seja necessária, por exemplo, em uma solução de inventário local que é usada somente em um único computador.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importar o arquivo de banco de dados para um projeto
 Para importar o arquivo de banco de dados para o seu projeto, use o **Assistente de configuração de fonte de dados** para criar uma fonte com base no arquivo de banco de dado. O assistente adiciona o arquivo de banco de dados e um dataset tipado ao seu projeto.

## <a name="deploy-the-database-file"></a>Implantar o arquivo de banco de dados
 O **Assistente de configuração de fonte de dados** usa um caminho relativo para criar conexões com o arquivo de banco de dado local. Isso permite que você copie a solução de um computador para outro se mantiver as posições relativas dos arquivos.

 Se você implantar sua solução em um servidor e, em seguida, distribuir o documento para cada usuário final, também deverá distribuir manualmente o arquivo de banco de dados e instalá-lo na mesma posição relativa ao documento. Isso significa que o usuário final não pode mover o documento para um novo local em seu computador, a menos que ele também mova o arquivo de banco de dados.

## <a name="local-database-files-and-caching-the-dataset"></a>Arquivos de banco de dados local e armazenando em cache o DataSet
 Em soluções de nível de documento para Microsoft Office Excel e Microsoft Office Word, você pode armazenar em cache os conjuntos de armazenamento no documento marcando a instância do conjunto de linhas com o atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Quando você adiciona o arquivo de banco de dados ao seu projeto usando o **Assistente de configuração de fonte de dados**, um dataset tipado é adicionado automaticamente ao seu projeto. Raramente é necessário aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a esse conjunto de dados, pois eles já são locais no computador do usuário. Para obter mais informações, consulte [armazenar dados em cache](../vsto/caching-data.md).

## <a name="see-also"></a>Confira também
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Como: popular documentos com dados de um banco de dado](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Como: atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Dados de cache](../vsto/caching-data.md)
