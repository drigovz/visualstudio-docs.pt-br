---
title: Avisos e Erros XAML
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 968e4167da1f8fd9bce21784a011d970014e1b4e
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467551"
---
# <a name="xaml-errors-and-warnings"></a>Avisos e erros de XAML

Ao criar XAML, o Visual Studio analisa o código conforme você digita. Um rabisco aparece em uma linha de código quando um erro é detectado. Se você passar o mouse sobre o rabisco, verá mais informações sobre o erro ou aviso. Para alguns erros e avisos, é exibida uma lâmpada de ação rápida e o uso de **Ctrl** + **.** o atalho de teclado exibe as opções para corrigir o problema.

## <a name="error-types"></a>Tipos de erro

Em segundo plano, várias ferramentas analisam o XAML em paralelo. Erros de XAML são categorizados em um dos três seguintes tipos, com base na ferramenta que detectou o erro:

|**Erro detectado por**|**Formato do código de erro**|**Versão do Visual Studio**|
| - |-----------------| - |
|Serviço de linguagem XAML (Editor XAML)|XLSxxxx| Todas as versões |
|XAML Designer|XDGxxxx| Todas as versões | 
|Editar XAML e Continuar|XECxxxx| Visual Studio 2019 versão 16,1 ou anterior |
|Recarga Dinâmica de XAML | XHRxxxx | Visual Studio 2019 versão 16,2 ou posterior |

Para obter mais detalhes sobre a remarcação do XAML editar & continuar como o Hot recarregamento de XAML, consulte nossas [notas de versão](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> Nem todos os erros ou avisos têm um código correspondente. Geralmente, esses erros são do XAML Designer.

## <a name="suppress-xaml-designer-errors"></a>Suprimir erros do XAML Designer

Abra a caixa de diálogo **Opções** selecionando **Ferramentas > Opções** e, em seguida, selecione **Editor de Texto > XAML > Diversos**.

Desmarque a caixa de seleção **Mostrar erros detectados pelo XAML Designer**.

![Suprimir erros do XAML Designer](media/suppress_xaml_designer_errors.png)
