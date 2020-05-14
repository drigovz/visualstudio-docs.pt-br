---
title: DesmontagemData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737278"
---
# <a name="disassemblydata"></a>DisassemblyData
Descreve uma instrução de desmontagem para o ambiente de desenvolvimento integrado (IDE) a ser exibido.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Membros
`dwFields`\
A [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) constante que especifica quais campos são preenchidos.

`bstrAddress`\
O endereço como um deslocamento de algum ponto de partida (geralmente o início da função associada).

`bstrCodeBytes`\
O código bytes para esta instrução.

`bstrOpcode`\
O código para esta instrução.

`bstrOperands`\
Os operands para esta instrução.

`bstrSymbol`\
O nome símbolo, se houver, associado ao endereço (símbolo público, rótulo e assim por diante).

`uCodeLocationId`\
O identificador de localização de código para esta linha desmontada. Se o endereço de contexto de código de uma linha for maior que o endereço de contexto de código de outra, então o identificador de localização de código desmontado da primeira também será maior do que o identificador de localização de código da segunda.

`posBeg`\
O [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde à posição em um documento onde os dados de desmontagem começam.

`posEnd`\
O [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde à posição em um documento onde os dados de desmontagem terminam.

`bstrDocumentUrl`\
Para documentos de texto que podem `bstrDocumentUrl` ser representados como nomes de arquivo, o campo é `file://file name`preenchido com o nome do arquivo onde a fonte pode ser encontrada, usando o formato .

Para documentos de texto que não `bstrDocumentUrl` podem ser representados como nomes de arquivo, é um identificador exclusivo para o documento, e o mecanismo de depuração deve implementar o método [GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Este campo também pode conter informações adicionais sobre as somas de cheques. Consulte observações para obter detalhes.

`dwByteOffset`\
O número de bytes da instrução é desde o início da linha de código.

`dwFlags`\
A [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) constante que especifica quais sinalizadores estão ativos.

## <a name="remarks"></a>Comentários
Cada `DisassemblyData` estrutura descreve uma instrução de desmontagem. Uma matriz dessas estruturas é devolvida a partir do método [Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

A estrutura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) é usada apenas para documentos baseados em texto. O intervalo de código fonte para esta instrução é preenchido apenas para a `dwByteOffset == 0`primeira instrução gerada a partir de uma instrução ou linha, por exemplo, quando .

Para documentos que não são texmários, um contexto de documento `bstrDocumentUrl` pode ser obtido a partir do código, e o campo deve ser um valor nulo. Se `bstrDocumentUrl` o campo for `bstrDocumentUrl` o mesmo `DisassemblyData` que o campo `bstrDocumentUrl` no elemento de matriz anterior, defina o valor nulo.

Se `dwFlags` o campo `DF_DOCUMENT_CHECKSUM` tiver o conjunto de bandeiras, então as `bstrDocumentUrl` informações adicionais de soma de cheques seguem a seqüência apontada pelo campo. Especificamente, após o exterminador de seqüência nulo, segue-se um GUID identificando o algoritmo de soma de verificação que, por sua vez, é seguido por um valor de 4 bytes indicando o número de bytes no soma de verificação e que, por sua vez, é seguido pelos bytes de soma de cheques. Veja o Exemplo neste tópico sobre como codificar [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]e decodificar este campo em .

## <a name="example"></a>Exemplo
O `bstrDocumentUrl` campo pode conter informações adicionais `DF_DOCUMENT_CHECKSUM` que não uma string se o sinalizador estiver definido. O processo de criação e leitura desta [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]seqüência codificada é simples em . No entanto, em [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], é outra questão. Para aqueles que estão curiosos, o exemplo a seguir [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] mostra uma maneira de criar a [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]seqüência codificada de e uma maneira de decodificar a seqüência codificada em .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
