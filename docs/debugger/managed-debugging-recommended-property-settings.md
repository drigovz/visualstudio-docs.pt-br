---
title: Configurações de Propriedade do depurador recomendadas para C#, VB | Microsoft Docs
description: Consulte as configurações de propriedade de compilação e compilação que devem ser as mesmas para toda a depuração gerenciada. Outras configurações podem variar dependendo do tipo de projeto.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b3061823a97faa53680bb358475a583493be5b93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893094"
---
# <a name="managed-debugging-recommended-property-settings"></a>Depuração gerenciada: configurações de propriedade recomendadas
Certas propriedades devem ser definidas da mesma maneira para todos os cenários gerenciados de depuração.

 As tabelas a seguir exibem as configurações de propriedade recomendadas.

 As configurações não listadas aqui podem variar entre os diferentes tipos de projeto gerenciados. Por exemplo, **Iniciar Ação** será definido de maneira diferente em um projeto do Windows Forms do que em um projeto do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>As propriedades de configuração na compilação (C#) ou na guia Compilar (Visual Basic)

|**Nome da propriedade**|**Configuração**|
|-----------------------|-----------------|
|**Definir constante de depuração**|C# e F#: defina a caixa de seleção como verificado. Isso permite que o aplicativo use uma classe de Depuração.|
|**Definir a constante TRACE**|C# e F#: defina a caixa de seleção como verificado. Isso permite que o aplicativo use uma classe de rastreamento.|
|**Otimizar código**|F#, C# e Visual Basic: definidos como falso. O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, habilite essa configuração, mas lembre-se de que o código exibido na janela **Desmontagem** será gerado da origem otimizada que pode não corresponder ao que aparece no Editor de Códigos. Para depurar um código otimizado, você deve desativar o Apenas Meu Código. (Confira [Restringir a depuração a Apenas Meu Código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Para obter mais informações, consulte [configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [configurações de projeto para uma configuração de depuração de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Caminho de saída**|Definido para bin\Debug\\.|
|**Opções compiladas avançadas**|Somente Visual Basic. Clique em **Avançado** para definir as propriedades avançadas descritas na tabela a seguir.|

### <a name="advanced-compiler-settings-dialog-box"></a>Caixa de diálogo de Configurações Avançadas do Compilador

|**Nome da propriedade**|**Configuração**|
|-----------------------|-----------------|
|**Habilitar otimizações**|Defina como false pelos motivos especificados na opção **otimizar código** na tabela anterior.|
|**Gerar informações de depuração**|Marque esta caixa de seleção para que o sinalizador /DEBUG seja definido ao compilar, o que vai gerar as informações necessárias para facilitar a depuração.|
|**Definir constante de depuração**|Marque esta caixa de seleção para definir a constante de `DEBUG`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Debug>.|
|**Definir a constante TRACE**|Marque esta caixa de seleção para definir a constante de `TRACE`, que permite que seu aplicativo use a classe <xref:System.Diagnostics.Trace>.|

## <a name="see-also"></a>Consulte também
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
- [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)