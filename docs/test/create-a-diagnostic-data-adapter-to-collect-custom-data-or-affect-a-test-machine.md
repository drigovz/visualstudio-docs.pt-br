---
title: Criar um adaptador de dados de diagnóstico para teste
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 800e866e2bfa915590060b09a98539533460bed3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965646"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Criar um adaptador de dados de diagnóstico para coletar dados personalizados ou afetar um computador de teste

É possível criar seu próprio adaptador de dados de diagnóstico para coletar dados quando você executar um teste, ou afetar o computador de teste como parte de seu teste. Por exemplo, você pode coletar os arquivos de log que são criados por seu aplicativo em teste e anexá-los aos resultados do teste, ou pode executar os testes quando há espaço limitado em disco no computador. Usando APIs fornecidas no Visual Studio Enterprise, você pode gravar código para executar tarefas em pontos específicos da execução de teste. Por exemplo, você pode executar tarefas quando um teste é iniciado, antes e depois da execução de cada teste individual, e quando o teste termina.

Você pode fornecer as informações padrão para o adaptador de dados de diagnóstico personalizado usando um arquivo de parâmetros de configuração. Por exemplo, você pode fornecer informações sobre o local do arquivo que deseja coletar e anexar aos resultados do teste, ou quanto espaço em disco você deseja deixar no sistema. Esses dados podem ser configurados para cada parâmetro de teste criado. Eles podem ser exibidos e editados usando o editor padrão fornecido com o Microsoft Test Manager ou você pode criar seu próprio controle de usuário para usar como editor. Todas as alterações feitas na configuração do adaptador no editor são armazenadas com as configurações de teste.

Se você estiver executando seus testes do Visual Studio, deverá definir essas configurações de teste como ativas. Para obter mais informações sobre as configurações de teste, confira [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tarefas

Use os tópicos a seguir como auxílio para criar adaptadores de dados de diagnóstico:

|Tarefas|Tópicos associados|
|-|-----------------------|
|**Criando um adaptador de dados de diagnóstico:** Você cria um adaptador de dados de diagnóstico criando uma biblioteca de classes e, em seguida, usa as APIs do adaptador de dados de diagnóstico para coletar as informações desejadas ou afetar um sistema de teste usado para executar os testes.|-   [Como: Criar um adaptador de dados de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Selecionando um adaptador de dados de diagnóstico personalizado para uso durante a execução dos testes:** Você pode selecionar qual adaptador de dados de diagnóstico será usado para as configurações do teste, para que o adaptador seja usado quando você executar os testes.|-   [Coletar dados de diagnóstico durante testes (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Coletar dados de diagnóstico em testes manuais (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Consulte também

- [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md)