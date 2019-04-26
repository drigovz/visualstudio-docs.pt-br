---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 479f7e1cbd85c0421497020ae1fc108154ca639a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968308"
---
# <a name="targetclr"></a>TargetCLR
A opção **TargetCLR** especifica a versão do CLR (Common Language Runtime) cujo perfil deverá ser criado quando mais de uma versão do CLR for carregada em um aplicativo.

 Por padrão, as Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] têm como destino a primeira versão do CLR carregada pelo aplicativo.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parâmetros
 `ClrVersion` O número de versão do CLR. Use o formato de versão **vN.N.NNNNN**.

## <a name="required-options"></a>Opções obrigatórias
 A opção **TargetCLR** pode ser usada somente com as opções de **Inicialização** ou **Anexar**.

 **Iniciar:** `AppName` Inicia o aplicativo especificado e a criação de perfil.

 **Anexar:** `PID` Inicia a criação de perfil do processo especificado.

## <a name="example"></a>Exemplo
 Nesse exemplo, a opção TargetCLR é usada para garantir que a versão 4.0.11003 do CLR tenha um perfil criado.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```