---
title: Solucionar problemas de modelos de projeto e de item
description: Saiba como solucionar problemas de modelos quando eles falharem ao carregar no ambiente de desenvolvimento.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 842e34ce18767f5d16cc55d16b8346369fe6cef9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869109"
---
# <a name="how-to-troubleshoot-templates"></a>Como solucionar problemas de modelos

Se houver falha no carregamento de um modelo no ambiente de desenvolvimento, haverá várias maneiras de localizar o problema.

## <a name="validate-the-vstemplate-file"></a>Validar o arquivo vstemplate

::: moniker range="vs-2017"

Se o arquivo *.vstemplate* em um modelo não estiver de acordo com o esquema de modelo do Visual Studio, o modelo poderá não aparecer na caixa de diálogo **Novo Projeto**.

::: moniker-end

::: moniker range=">=vs-2019"

Se o arquivo *.vstemplate* em um modelo não estiver de acordo com o esquema de modelo do Visual Studio, o modelo poderá não aparecer na caixa de diálogo em que você cria projetos.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Para validar o arquivo vstemplate

1. Localize o arquivo *.zip* que contém o modelo.

1. Extraia o arquivo *. zip* .

1. No menu **Arquivo** do Visual Studio, escolha **Abrir** > **Arquivo**.

1. Selecione o arquivo *vstemplate* para o modelo e escolha **Abrir**.

1. Verifique se o XML do arquivo *vstemplate* adota o esquema de modelo. Para obter mais informações sobre o esquema do *vstemplate*, consulte [Template schema reference](../extensibility/visual-studio-template-schema-reference.md) (Referência de esquema de modelo).

    > [!NOTE]
    > Para obter suporte do IntelliSense enquanto cria o arquivo *vstemplate*, adicione um atributo `xmlns` ao elemento `VSTemplate` e atribua um valor igual a `http://schemas.microsoft.com/developer/vstemplate/2005`.

1. Salve e feche o arquivo *vstemplate*.

1. Selecione os arquivos incluídos no modelo, clique com o botão direito do mouse e escolha **Enviar para**  >  **pasta compactada (zipada)**. Os arquivos que você selecionou são compactados em um arquivo *. zip* .

1. Insira o novo arquivo *.zip* no mesmo diretório do antigo arquivo *.zip*.

1. Exclua os arquivos de modelo extraídos e o arquivo *.zip* de modelo antigo.

## <a name="enable-diagnostic-logging"></a>Habilitar registro em log de diagnóstico

Você pode habilitar o registro em log de diagnóstico para a descoberta de modelo, seguindo as etapas em [Solucionando problemas de descoberta do modelo (extensibilidade)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Confira também

- [Solucionar problemas de descoberta do modelo (extensibilidade)](../extensibility/troubleshooting-template-discovery.md)
- [Personalizar modelos](../ide/customizing-project-and-item-templates.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema de modelo](../extensibility/visual-studio-template-schema-reference.md)
