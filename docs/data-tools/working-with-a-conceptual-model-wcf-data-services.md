---
title: Trabalhando com um modelo conceitual (WCF Data Services)
description: Trabalhar com um modelo conceitual no WCF Data Services. Consultar dados por meio de objetos em vez de converter entre esquemas de banco de dado e modelos de objetos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ef5745f974848da75b4dcc0c42b59b38aa61cd0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866106"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Trabalhar com um modelo conceitual (WCF Data Services)

Ao usar um modelo conceitual para descrever os dados em um banco de dado, você pode consultar dados por meio de seus objetos em vez de ter que fazer a conversão entre um esquema de banco de dados e um modelo de objeto.

Você pode usar modelos conceituais com WCF Data Services aplicativos. Os tópicos a seguir mostram como consultar dados por meio de um modelo conceitual.

| Tópico | Descrição |
| - | - |
| [Como executar consultas de serviço de dados](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Mostra como consultar um serviço de dados de um aplicativo .NET. |
| [Como: resultados da consulta de projeto](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Mostra como reduzir a quantidade de dados retornados por meio de uma consulta de serviço de dados. |

Ao usar um modelo conceitual, você pode definir que tipo de dados é válido no idioma que corresponde ao seu domínio. Você pode definir dados válidos no modelo ou pode adicionar validação às operações que você executa em uma entidade ou serviço de dados.

Os tópicos a seguir mostram como adicionar validação a aplicativos WCF Data Services.

|Tópico|Descrição|
|-----------|-----------------|
|[Como interceptar mensagens de serviço de dados](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Mostra como adicionar validação a uma operação de serviço de dados.|

 Os tópicos a seguir mostram como criar, atualizar e excluir dados executando operações em entidades.

|Tópico|Descrição|
|-----------|-----------------|
|[Como: Adicionar, modificar e excluir entidades](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Mostra como criar, atualizar e excluir dados de entidade em um serviço de dados.|
|[Como definir relações de entidade](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Mostra como criar ou alterar relações em um serviço de dados.|

## <a name="see-also"></a>Confira também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Consultar o serviço de dados](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
