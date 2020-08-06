---
title: SetServiceAccount メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6087a531802a7752ea794a44147c79fb7c3fa3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712873"
---
# <a name="setserviceaccount-method-sqlservice-class"></a><span data-ttu-id="b5013-102">SetServiceAccount メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="b5013-102">SetServiceAccount Method (SqlService Class)</span></span>
  <span data-ttu-id="b5013-103">サーバー インスタンスの実行環境に対応するユーザー名およびパスワードを変更します。</span><span class="sxs-lookup"><span data-stu-id="b5013-103">Attempts to change the user name and password that the service instance runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5013-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5013-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b5013-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="b5013-105">Parts</span></span>  
 <span data-ttu-id="b5013-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b5013-106">*object*</span></span>  
 <span data-ttu-id="b5013-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b5013-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b5013-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5013-108">Parameters</span></span>  
 <span data-ttu-id="b5013-109">*ServiceStartName*</span><span class="sxs-lookup"><span data-stu-id="b5013-109">*ServiceStartName*</span></span>  
 <span data-ttu-id="b5013-110">サービスの実行環境に対応するアカウント名を指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="b5013-110">A string value that specifies the account name that the service runs under.</span></span> <span data-ttu-id="b5013-111">サービスの種類によっては、アカウント名が "ドメイン名\ユーザー名" の形式になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b5013-111">Depending on the service type, the account name might be in the form of DomainName\Username.</span></span> <span data-ttu-id="b5013-112">サービス プロセスの実行時には、ログオンは次のいずれかの形式になります。</span><span class="sxs-lookup"><span data-stu-id="b5013-112">When it runs, the service process will be logged using one of two forms:</span></span>  
  
-   <span data-ttu-id="b5013-113">アカウントがビルトイン ドメインに属している場合、\Username を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="b5013-113">If the account belongs to the built-in domain, \Username can be specified.</span></span>  
  
-   <span data-ttu-id="b5013-114">NULL を指定した場合、サービスは**LocalSystem**アカウントとしてログオンします。</span><span class="sxs-lookup"><span data-stu-id="b5013-114">If NULL is specified, the service will be logged on as the **LocalSystem** account.</span></span>  
  
 <span data-ttu-id="b5013-115">カーネルまたはシステムレベルのドライバーの場合、 *StartName*にはドライバーオブジェクト名 (\ Filesystem\r dr または \Driver\Xns) が含まれます。この名前は、i/o システムがデバイスドライバーを読み込むために使用します。</span><span class="sxs-lookup"><span data-stu-id="b5013-115">For kernel or system-level drivers, *StartName* contains the driver object name, either \FileSystem\Rdr or \Driver\Xns, which the I/O system uses to load the device driver.</span></span> <span data-ttu-id="b5013-116">NULL が指定された場合、ドライバーは、I/O システムがサービス名に基づいて作成した既定のオブジェクト名 (たとえば、DWDOM\Admin) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="b5013-116">If NULL is specified, the driver runs with a default object name created by the I/O system based on the service name, for example, DWDOM\Admin.</span></span>  
  
 <span data-ttu-id="b5013-117">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="b5013-117">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="b5013-118">*StartName*パラメーターのアカウント名のパスワードを示す文字列値です。</span><span class="sxs-lookup"><span data-stu-id="b5013-118">A string value that specifies the password for the account name in the *StartName* parameter.</span></span> <span data-ttu-id="b5013-119">パスワードを変更しない場合は NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5013-119">Specify NULL if you are not changing the password.</span></span> <span data-ttu-id="b5013-120">サービスがパスワードを持っていない場合は、空の文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5013-120">Specify an empty string if the service has no password.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b5013-121">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="b5013-121">Property Value/Return Value</span></span>  
 <span data-ttu-id="b5013-122">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。</span><span class="sxs-lookup"><span data-stu-id="b5013-122">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="b5013-123">それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="b5013-123">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5013-124">解説</span><span class="sxs-lookup"><span data-stu-id="b5013-124">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5013-125">参照</span><span class="sxs-lookup"><span data-stu-id="b5013-125">See Also</span></span>  
 <span data-ttu-id="b5013-126">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b5013-126">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
