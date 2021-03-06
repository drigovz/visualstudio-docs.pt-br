---
title: Estender testes de IU codificados e gravações da ação
description: Saiba como criar uma extensão para a estrutura de teste de interface do usuário codificada para sua interface do usuário específica aproveitando a extensibilidade da estrutura de teste de interface do usuário codificada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c4a846fe9425af7dc62ef93276c0272f480b7f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949864"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Estender testes de IU codificados e gravações da ação

A estrutura de teste para testes de IU codificados e gravações da ação não dá suporte a todas as interfaces do usuário possíveis. Ele pode não dar suporte à interface do usuário específica que você deseja testar. Por exemplo, não é possível criar imediatamente um teste de IU codificado ou uma gravação da ação para uma planilha do Microsoft Excel. No entanto, é possível criar sua própria extensão para a estrutura de teste de IU codificado compatível com a interface do usuário específica, aproveitando a extensibilidade da estrutura do teste de IU codificado.

![Arquitetura de teste de IU](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Extensão de exemplo para testar o Microsoft Excel

Essa [postagem no blog](/archive/blogs/gautamg/3-introducing-sample-excel-extension) contém um link para uma [extensão de exemplo](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) para a estrutura do teste de IU codificado. Também é possível exibir toda a [série de postagens no blog para extensibilidade do teste de IU codificado](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility).

> [!NOTE]
> A amostra é destinada para uso com o Microsoft Excel 2010. Ela pode funcionar ou não com outras versões do Excel.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Usar a automação da interface do usuário para testar o código](../test/use-ui-automation-to-test-your-code.md)
- [Práticas recomendadas para testes de IU codificados](../test/best-practices-for-coded-ui-tests.md)
- [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ação](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)