---
layout: single
title:  "AutoGPT Forge: Chế tạo logic tác nhân thông minh"
desc: ""
keywords: "autoGPT"
categories: [AI]
tag: [AI]
---

AutoGPT Forge: Chế tạo logic tác nhân thông minh
=====================================================

![](https://miro.medium.com/v2/resize:fit:700/1*Ls2N3NmJrVSdod9MZXsPxw.png)

Xin chào những người đam mê AI! Hôm nay, chúng ta sắp bắt đầu một hành trình khai sáng để tạo ra logic tác nhân thông minh. Đây là phần 4 trong loạt bài hướng dẫn sử dụng AutoGPT Forge, bạn có thể tìm thấy các phần trước tại đây:

Phần 1: [AutoGPT Forge: Hướng dẫn toàn diện cho bước đầu tiên của bạn](/ai/autoGPT-part1-a-comprehensive-guide)

Phần 2: [AutoGPT Forge: Bản thiết kế của một đặc vụ AI](/ai/autoGPT-part2-the-blueprint-of-an-ai-agent)

Phần 3: [AutoGPT Forge: Tương tác với Đại lý của bạn](/ai/autoGPT-part3-interacting-with-your-agent)

Được rồi, các bạn, hãy đi thẳng vào phần thú vị: viết mã! Chúng tôi sắp thiết lập một hệ thống tiện lợi giới thiệu cách sử dụng LLM làm nguồn lực trí tuệ đằng sau đại lý của chúng tôi. Nhiệm vụ? Để giải quyết nhiệm vụ đơn giản là ghi thủ đô của Hoa Kỳ vào một tệp txt. Phần thú vị nhất? Chúng tôi sẽ không đưa ra từng bước cho đại lý của mình. Thay vào đó, chúng ta sẽ chỉ giao nhiệm vụ: “Viết từ 'Washington' vào một tệp .txt,” và kinh ngạc nhìn nó tự tìm ra 'cách thực hiện', sau đó nhanh chóng thực hiện các lệnh cần thiết. Thật tuyệt vời phải không?

**Thiết lập dự án Đại lý thông minh của bạn**
=============================================

Trước khi bắt tay vào thực hiện, hãy đảm bảo rằng bạn đã chuẩn bị sẵn dự án của mình và tạo nhân viên hỗ trợ như chi tiết trong hướng dẫn bắt đầu của chúng tôi. Bỏ lỡ bước đó? Đừng lo lắng! Chỉ cần chuyển sang thiết lập dự án bằng cách [nhấp vào đây](/ai/autoGPT-part1-a-comprehensive-guide) . Khi bạn đã sẵn sàng xong, hãy quay lại và chúng ta sẽ bắt đầu chạy.

Trong ảnh chụp màn hình sau, bạn sẽ nhận thấy tôi đã tạo một tác nhân có tên “ **SmartAgent** ” và sau đó truy cập vào `agent.py`tệp nằm trong thư mục con 'forge'. Đây sẽ là không gian làm việc của chúng tôi để tích hợp logic điều khiển LLM. Trong khi [hướng dẫn trước](/ai/autoGPT-part2-the-blueprint-of-an-ai-agent) của chúng tôi đã đề cập đến cách bố trí dự án và hoạt động của đại lý, đừng lo lắng! Tôi sẽ nêu bật những điểm cần thiết khi chúng ta đi sâu vào việc triển khai logic.

![](https://miro.medium.com/v2/resize:fit:1461/1*WkE_jU8MXNzULwThFJJixg.png)

Vòng đời nhiệm vụ
=================

Vòng đời của một tác vụ, từ khi tạo đến khi thực thi, được nêu trong giao thức tác nhân. Nói một cách đơn giản: một nhiệm vụ được bắt đầu, các bước của nó được thực hiện một cách có hệ thống và kết thúc sau khi hoàn thành.

Muốn đại lý của bạn thực hiện một hành động? Bắt đầu bằng cách gửi một `create_task` yêu cầu. Bước quan trọng này liên quan đến việc chỉ định chi tiết nhiệm vụ, giống như cách bạn gửi lời nhắc tới ChatGPT bằng cách sử dụng `input` trường này. Nếu bạn tự mình thực hiện việc này thì giao diện người dùng là người bạn tốt nhất của bạn; nó thay mặt bạn xử lý dễ dàng tất cả lệnh gọi API.

Khi đại lý của bạn nhận được thông tin này, nó sẽ kích hoạt `create_task` chức năng. Phương pháp này `super().create_task(task_request)` thay mặt bạn quản lý dễ dàng tất cả việc lưu giữ hồ sơ giao thức cần thiết. Sau đó, nó chỉ ghi lại quá trình tạo tác vụ. Đối với phạm vi của hướng dẫn này, không cần phải điều chỉnh chức năng này.

```python
async def create_task(self, task_request: TaskRequestBody) -> Task:
    """
    Giao thức tác nhân, là cốt lõi của Forge, hoạt động bằng cách tạo một tác vụ và sau đó
    thực hiện các bước cho tác vụ đó. Phương thức này được gọi khi tác nhân được được yêu cầu tạo
    một tác vụ.

    Chúng tôi đang kết nối vào chức năng để thêm một thông điệp tường trình tùy chỉnh. Mặc dù bạn có thể làm bất cứ điều gì bạn muốn ở đây.
    """
    task = await super().create_task(task_request)
    LOG.info(
        f"📦 Task created: {task.task_id} input: {task.input[:40]}{'...' if len(task.input) > 40 else ''}"
    )
    return task
```

Khi một tác vụ được bắt đầu, `execute_step` hàm sẽ được gọi liên tục cho đến khi bước cuối cùng được thực thi. Dưới đây là giao diện ban đầu của `execute_step`, và lưu ý rằng tôi đã bỏ qua phần giải thích chuỗi tài liệu dài dòng để cho ngắn gọn, nhưng bạn sẽ gặp nó trong dự án của mình.

```python
async def execute_step(self, task_id: str, step_request: StepRequestBody) -> Step:
    # An example that
      step = await self.db.create_step(
          task_id=task_id, input=step_request, is_last=True
      )

      self.workspace.write(task_id=task_id, path="output.txt", data=b"Washington D.C")


      await self.db.create_artifact(
          task_id=task_id,
          step_id=step.step_id,
          file_name="output.txt",
          relative_path="",
          agent_created=True,
      )

      step.output = "Washington D.C"

      LOG.info(f"\t✅ Final Step completed: {step.step_id}")

      return step
```

Đây là những gì bạn đang chứng kiến: một cách thông minh để vượt qua bài kiểm tra 'ghi tập tin', được chia thành bốn giai đoạn rõ ràng:

1.  **Tạo bước cơ sở dữ liệu:** Giai đoạn đầu tiên là tạo một bước trong cơ sở dữ liệu, một khía cạnh thiết yếu của giao thức tác nhân. Bạn sẽ nhận thấy rằng trong khi thiết lập bước này, chúng tôi đã gắn cờ nó bằng `is_last=True`. Điều này báo hiệu cho giao thức tác nhân rằng không còn bước nào đang chờ xử lý. Với mục đích của hướng dẫn này, chúng ta hãy giả định rằng nhân viên hỗ trợ của chúng tôi sẽ chỉ giải quyết các nhiệm vụ một bước. Tuy nhiên, hãy chờ đợi các hướng dẫn trong tương lai, nơi chúng tôi sẽ thăng cấp và để nhân viên xác định điểm hoàn thành.
2.  **Viết tệp:** Tiếp theo, chúng tôi viết ra “Washington DC” bằng cách sử dụng `workspace.write` chức năng này. Đơn giản phải không?
3.  **Cập nhật cơ sở dữ liệu tạo tác:** Sau khi tệp được ghi, đã đến lúc ghi tệp này vào cơ sở dữ liệu tạo tác của tác nhân, đảm bảo mọi thứ đều được ghi lại.
4.  Ghi **nhật ký và cài đặt đầu ra bước:** Để kết thúc mọi thứ, chúng tôi căn chỉnh đầu ra bước với những gì chúng tôi đã viết trong tệp, ghi lại nhật ký rằng bước của chúng tôi đã được thực hiện và sau đó đưa đối tượng bước vào hoạt động.

Bây giờ chúng ta đã làm sáng tỏ quy trình để vượt qua bài kiểm tra 'ghi tệp', đã đến lúc cải tiến mọi thứ lên một tầm cao mới. Hãy biến nó thành một tác nhân thực sự thông minh, trao quyền cho nó điều hướng và chinh phục thử thách một cách tự chủ. Sẵn sàng để đi sâu vào?

Xây dựng nền tảng cho Đại lý thông minh của chúng tôi
=====================================================

Được rồi, mệnh lệnh kinh doanh đầu tiên: Hãy loại bỏ `excuse_step` chức năng táo bạo đó khỏi logic lừa đảo của nó và đặt nền móng cho tác nhân thông minh của chúng ta. Hãy nhớ rằng, khi `execute_step` hàm của chúng ta nhận được lệnh gọi, ban đầu nó không biết gì về nhiệm vụ cụ thể hiện tại. Vì vậy, nhiệm vụ ban đầu của chúng tôi là khắc phục điều này.

Để thu hẹp khoảng cách kiến ​​thức này, chúng tôi sẽ triệu tập các chi tiết nhiệm vụ bằng cách sử dụng thông tin `task_id` được cung cấp. Đây là đoạn mã kỳ diệu để biến điều đó thành hiện thực:

```python
task = await self.db.get_task(task_id)
```

Ngoài ra, chúng tôi không quên bước quan trọng là tạo bản ghi cơ sở dữ liệu. Như chúng tôi đã làm trước đây, chúng tôi sẽ nhấn mạnh đây là nhiệm vụ chỉ thực hiện một lần với `is_last=True`:

```python
step = await self.db.create_step(
    task_id=task_id, input=step_request, is_last=True
)
```

Với những bổ sung này, `execute_step`hàm của bạn giờ đây sẽ có cấu trúc tối giản nhưng cần thiết:

```python
async def execute_step(self, task_id: str, step_request: StepRequestBody) -> Step:
    # Firstly we get the task this step is for so we can access the task input
    task = await self.db.get_task(task_id)

    # Create a new step in the database
    step = await self.db.create_step(
        task_id=task_id, input=step_request, is_last=True
    )
    return step
```

Với những viên gạch nền tảng đã được đặt ra này, chúng ta hãy bắt tay vào một điều thực sự hấp dẫn: giới thiệu, The **NhắcEngine** .

Nghệ thuật thúc giục
====================

![](https://miro.medium.com/v2/resize:fit:700/1*wY6m7gi6BH8Z__-_zwoXFg.png)

Nhắc 101

Lời nhắc giống như một người thợ thủ công tỉ mỉ định hình các thông điệp phù hợp với các mô hình ngôn ngữ mạnh mẽ như ChatGPT. Với việc những mô hình này rất phù hợp với các sắc thái đầu vào, việc thiết kế lời nhắc hoàn hảo để khơi gợi hành vi gây kinh ngạc có thể là một thách thức như mê cung. Nhập: **NhắcEngine** .

Mặc dù “ _PromptEngine_ ” nghe có vẻ cao cấp nhưng bản chất của nó lại đơn giản một cách trang nhã. Nó cho phép bạn lưu trữ lời nhắc của mình trong tệp văn bản hoặc chính xác hơn là trong các mẫu Jinja2. Lợi thế? Bạn có thể tinh chỉnh các lời nhắc được đưa ra cho đại lý của mình mà không cần đi sâu vào mã. Ngoài ra, nó còn mang đến sự linh hoạt để tùy chỉnh lời nhắc cho các LLM cụ thể. Hãy phá vỡ điều này.

Đầu tiên, tích hợp NhắcEngine từ SDK:

```python
from .sdk import PromptEngine
```

Tiếp theo, trong `execute_step` hàm của bạn, hãy khởi tạo công cụ phù hợp với `gpt-3.5-turbo` LLM:

```python
prompt_engine = PromptEngine("gpt-3.5-turbo")
```
Việc tải lời nhắc rất đơn giản. Ví dụ: việc tải `system-format` lời nhắc, chỉ ra định dạng phản hồi từ LLM, dễ dàng như sau:

```python
system_prompt = prompt_engine.load_prompt("system-format")
```

Đối với các trường hợp sử dụng phức tạp, như `task-step` lời nhắc yêu cầu tham số, hãy sử dụng phương pháp sau:

```python
# Define the task parameters
task_kwargs = {
    "task": task.input,
    "abilities": self.abilities.list_abilities_for_prompt(),
}

# Load the task prompt with the defined task parameters
task_prompt = prompt_engine.load_prompt("task-step", **task_kwargs)
```

Tìm hiểu sâu hơn, chúng ta hãy xem qua `task-step`mẫu lời nhắc có tại `prompts/gpt-3.5-turbo/task-step.j2`:

```python
{% extends "techniques/expert.j2" %}
{% block expert %}Planner{% endblock %}
{% block prompt %}
Your task is:

{{ task }}

Answer in the provided format.

Your decisions must always be made independently without seeking user assistance. Play to your strengths as an LLM and
pursue simple strategies with no legal complications.

{% if constraints %}
## Constraints
You operate within the following constraints:
{% for constraint in constraints %}
- {{ constraint }}
{% endfor %}
{% endif %}

{% if resources %}
## Resources
You can leverage access to the following resources:
{% for resource in resources %}
- {{ resource }}
{% endfor %}
{% endif %}

{% if abilities %}
## Abilities
You have access to the following abilities you can call:
{% for ability in abilities %}
- {{ ability }}
{% endfor %}
{% endif %}

{% if best_practices %}
## Best practices
{% for best_practice in best_practices %}
- {{ best_practice }}
{% endfor %}
{% endif %}
{% endblock %}
```

Mẫu này là một tuyệt tác về tính mô-đun, nó sử dụng [định dạng jinga2](https://jinja.palletsprojects.com/en/3.1.x/templates/) mạnh mẽ . Bằng cách sử dụng `extends`lệnh này, nó được xây dựng dựa trên `expert.j2`mẫu cơ sở. Các khối khác nhau – hạn chế, tài nguyên, khả năng và phương pháp hay nhất – cho phép lời nhắc động điều chỉnh dựa trên ngữ cảnh. Nó giống như một bản kế hoạch hội thoại, hướng dẫn LLM hiểu nhiệm vụ, tuân thủ các ràng buộc cũng như triển khai các nguồn lực và khả năng để đạt được kết quả mong muốn.

NhắcEngine trang bị cho chúng ta một công cụ mạnh mẽ để trò chuyện liền mạch với các mô hình ngôn ngữ lớn. Bằng cách đưa ra các lời nhắc bên ngoài và sử dụng các mẫu, chúng tôi có thể đảm bảo rằng tổng đài viên của mình vẫn linh hoạt, thích ứng với những thách thức mới mà không cần sửa đổi mã. Khi chúng ta tiến về phía trước, hãy ghi nhớ nền tảng này - đó là nền tảng cho trí thông minh của đặc vụ chúng ta.

Tương tác với LLM của bạn
=========================

Để khai thác triệt để các khả năng của LLMd, nó không chỉ đơn giản là gửi một lời nhắc đơn độc. Đó là về việc giao nhiệm vụ cho mô hình với một loạt các chỉ thị có cấu trúc. Để làm điều này, chúng tôi cần cấu trúc các lời nhắc của mình thành định dạng LLM của chúng tôi được thiết kế để xử lý danh sách các thông báo. Sử dụng `system_prompt`và `task_prompt`chúng tôi đã chuẩn bị trước đó để tạo danh sách tin nhắn:

```python
 messages = [
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": task_prompt}
        ]
```

Với lời nhắc của chúng tôi đã được định hình và sẵn sàng, đã đến lúc thực hiện LLM của chúng tôi! Mặc dù giai đoạn này đòi hỏi một số mã cơ bản, nhưng điểm nổi bật là `chat_completion_request`. Chức năng quan trọng này thực hiện nhiệm vụ LLM và truy xuất đầu ra của nó. Mã liền kề chỉ đóng gói yêu cầu của chúng tôi và giải mã phản hồi của mô hình:

```python
try:
      # Define the parameters for the chat completion request
      chat_completion_kwargs = {
          "messages": messages,
          "model": "gpt-3.5-turbo",
      }
      # Make the chat completion request and parse the response
      chat_response = await chat_completion_request(**chat_completion_kwargs)
      answer = json.loads(chat_response["choices"][0]["message"]["content"])

      # Log the answer for debugging purposes
      LOG.info(pprint.pformat(answer))

  except json.JSONDecodeError as e:
      # Handle JSON decoding errors
      LOG.error(f"Unable to decode chat response: {chat_response}")
  except Exception as e:
      # Handle other exceptions
      LOG.error(f"Unable to generate chat response: {e}")Step 7: Executing the Derived Ability
```

Việc điều hướng qua các điểm đặc biệt của đầu ra LLM để trích xuất một thông báo rõ ràng có thể xử lý được có thể là một nỗ lực mang nhiều sắc thái. Cách tiếp cận hiện tại của chúng tôi rất đơn giản và thường sẽ hoạt động với GPT-3.5 và GPT-4. Tuy nhiên, các hướng dẫn trong tương lai sẽ mở rộng tầm nhìn của bạn bằng những cách phức tạp hơn để xử lý kết quả đầu ra LLM. Mục đích? Để đảm bảo rằng bạn không chỉ bị giới hạn ở JSON, đặc biệt là khi một số LLM vượt trội với các mẫu phản hồi thay thế. Giữ nguyên!

Sử dụng và tạo ra khả năng
==========================

Đối với những người đặc biệt chú ý đến từng chi tiết, bạn có thể đã chọn tài liệu tham khảo về khả năng của nhân viên khi chúng ta thảo luận về việc tạo lời nhắc `task-step`. Khả năng là các bánh răng và đòn bẩy cho phép tác nhân tương tác với các nhiệm vụ trước mắt. Hãy cùng khám phá cơ chế đằng sau những khả năng này và cách bạn có thể khai thác và thậm chí mở rộng chúng.

Trong SDK, có một thư mục được chỉ định có tiêu đề `abilities`. Theo văn bản này, nó chứa `registry.py`, `finish.py`và một thư mục con có tên `file_system`. Và vẫn còn không gian để mở rộng – có lẽ khả năng đổi mới của bạn sẽ sớm xuất hiện ở đây!

Các tập tin `registry.py`đóng một vai trò quan trọng. Nó cung cấp kế hoạch chi tiết nền tảng cho các khả năng, tích hợp `@ability`trang trí thiết yếu và `AbilityRegister`lớp học. Lớp này không chỉ là một danh sách thụ động; đó là một danh mục hoạt động giúp theo dõi các khả năng sẵn có và mô tả chức năng cần thiết để thực hiện chúng. Hơn nữa, một thanh ghi khả năng mặc định được tích hợp liền mạch vào lớp Tác nhân cơ sở, giúp nó có thể truy cập dễ dàng thông qua tay `self.abilities`cầm. Điều này được thêm vào `Agent`lớp theo chức năng của nó `init`như sau:

```python
self.abilities = Khả năngĐăng ký(tự)
```

Trong khi `AbilityRegister`được tích hợp nhiều phương pháp tiện ích, có hai phương pháp nổi bật. Phương pháp này `list_abilities_for_prompt`quản lý và cấu trúc các khả năng để tích hợp nhanh chóng. Ngược lại, `run_ability`vận hành khả năng được chỉ định, chuyển nó từ mã sang hành động.

DNA của khả năng bao gồm một chức năng được tô điểm bằng `@ability`bộ trang trí và bắt buộc phải ghép nối với các tham số, đặc biệt là `agent`và `task_id`.

```python
@ability(
    name="write_file",
    description="Write data to a file",
    parameters=[
        {
            "name": "file_path",
            "description": "Path to the file",
            "type": "string",
            "required": True,
        },
        {
            "name": "data",
            "description": "Data to write to the file",
            "type": "bytes",
            "required": True,
        },
    ],
    output_type="None",
)
async def write_file(agent, task_id: str, file_path: str, data: bytes) -> None:
    pass
```

Ở đây, `@ability`trình trang trí không chỉ là một vật trang trí mà còn là một công cụ xác định chức năng. Nó bao gồm siêu dữ liệu của khả năng: nhận dạng ( `name`), chức năng ( `description`) và các tham số vận hành của khả năng. Mỗi tham số được mô tả một cách chính xác, gói gọn danh tính, kiểu dữ liệu và nhu cầu vận hành của nó.

Ví dụ về khả năng tùy chỉnh: Trình tìm nạp trang web
----------------------------------------------------

```python
import requests

@ability(
  name="fetch_webpage",
  description="Retrieve the content of a webpage",
  parameters=[
      {
          "name": "url",
          "description": "Webpage URL",
          "type": "string",
          "required": True,
      }
  ],
  output_type="string",
)
async def fetch_webpage(agent, task_id: str, url: str) -> str:
  response = requests.get(url)
  return response.text
```

Khả năng này, “ _fetch\_webpage_ ”, chấp nhận URL làm đầu vào và trả về nội dung HTML của trang web dưới dạng chuỗi. Như bạn có thể thấy, các khả năng tùy chỉnh cho phép bạn mở rộng liền mạch các chức năng cốt lõi của tổng đài viên, tích hợp các công cụ và thư viện bên ngoài để tăng cường khả năng của tổng đài viên.

Việc tạo ra một khả năng tùy chỉnh đòi hỏi sự tổng hợp giữa hiểu biết về kiến ​​trúc và năng lực kỹ thuật. Đó là về việc trình bày rõ ràng một chức năng, tranh thủ các tham số hoạt động của nó và kết hợp chúng một cách phức tạp với `@ability`các thông số kỹ thuật của người trang trí. Với các khả năng tùy chỉnh như "fetch\_webpage", tiềm năng của đặc vụ chỉ bị giới hạn bởi trí tưởng tượng của bạn, sẵn sàng giải quyết các nhiệm vụ phức tạp với năng lực tinh tế.

Chạy một khả năng
=================

Bây giờ bạn đã hiểu rõ bản chất của các khả năng và có đủ năng lực để tạo ra chúng, đã đến lúc áp dụng những kỹ năng này vào thực tế. Phần cuối cùng của câu đố của chúng tôi là `execute_step`chức năng. Mục tiêu của chúng tôi? Để giải thích phản ứng của tác nhân, hãy tách khả năng mong muốn và biến nó thành hiện thực.

Đầu tiên và quan trọng nhất, chúng tôi lấy được thông tin chi tiết về khả năng từ phản hồi của tác nhân. Điều này cho chúng ta một bức tranh rõ ràng về nhiệm vụ trước mắt:

```python
# Extract the ability from the answer
ability = answer["ability"]
```

Với thông tin chi tiết về khả năng trong tầm tay, bước tiếp theo là huy động nó. Điều này liên quan đến việc gọi `run_ability`hàm đã thảo luận trước đó của chúng ta

```python
# Run the ability and get the output
# We don't actually use the output in this example
output = await self.abilities.run_ability(
    task_id, ability["name"], **ability["args"]
)
```

Ở đây, chúng tôi đang gọi khả năng được chỉ định. Việc `task_id`đảm bảo tính liên tục, `ability['name']`xác định chính xác hàm và các đối số ( `ability["args"]`) cung cấp ngữ cảnh cần thiết.

Khi hoàn tất, chúng ta sẽ tạo đầu ra của bước này để phản ánh suy nghĩ của nhân viên hỗ trợ. Điều này không chỉ mang lại sự minh bạch mà còn cung cấp cái nhìn thoáng qua về quá trình ra quyết định của đại lý:

```python
# Set the step output to the "speak" part of the answer
step.output = answer["thoughts"]["speak"]

# Return the completed step
return step
```

Và bạn có nó rồi đấy! Tác nhân thông minh đầu tiên của bạn, được thiết kế với độ chính xác và mục đích, sẵn sàng đương đầu với thử thách. Sân khấu đã được dựng sẵn. Đến giờ diễn rồi!

Đây là chức năng của bạn sẽ trông như thế nào:

```python
async def execute_step(self, task_id: str, step_request: StepRequestBody) -> Step:
    # Firstly we get the task this step is for so we can access the task input
    task = await self.db.get_task(task_id)

    # Create a new step in the database
    step = await self.db.create_step(
        task_id=task_id, input=step_request, is_last=True
    )

    # Log the message
    LOG.info(f"\t✅ Final Step completed: {step.step_id} input: {step.input[:19]}")

    # Initialize the PromptEngine with the "gpt-3.5-turbo" model
    prompt_engine = PromptEngine("gpt-3.5-turbo")

    # Load the system and task prompts
    system_prompt = prompt_engine.load_prompt("system-format")

    # Initialize the messages list with the system prompt
    messages = [
        {"role": "system", "content": system_prompt},
    ]
    # Define the task parameters
    task_kwargs = {
        "task": task.input,
        "abilities": self.abilities.list_abilities_for_prompt(),
    }

    # Load the task prompt with the defined task parameters
    task_prompt = prompt_engine.load_prompt("task-step", **task_kwargs)

    # Append the task prompt to the messages list
    messages.append({"role": "user", "content": task_prompt})

    try:
        # Define the parameters for the chat completion request
        chat_completion_kwargs = {
            "messages": messages,
            "model": "gpt-3.5-turbo",
        }
        # Make the chat completion request and parse the response
        chat_response = await chat_completion_request(**chat_completion_kwargs)
        answer = json.loads(chat_response["choices"][0]["message"]["content"])

        # Log the answer for debugging purposes
        LOG.info(pprint.pformat(answer))

    except json.JSONDecodeError as e:
        # Handle JSON decoding errors
        LOG.error(f"Unable to decode chat response: {chat_response}")
    except Exception as e:
        # Handle other exceptions
        LOG.error(f"Unable to generate chat response: {e}")

    # Extract the ability from the answer
    ability = answer["ability"]

    # Run the ability and get the output
    # We don't actually use the output in this example
    output = await self.abilities.run_ability(
        task_id, ability["name"], **ability["args"]
    )

    # Set the step output to the "speak" part of the answer
    step.output = answer["thoughts"]["speak"]

    # Return the completed step
    return step
```

Tương tác với đại lý của bạn
============================

> ⚠️ Lưu ý: Giao diện người dùng và điểm chuẩn vẫn đang trong quá trình thử nghiệm nên có thể có một chút trục trặc.

Với khối lượng công việc nặng nhọc trong việc chế tạo Tác nhân thông minh đang ở phía sau, đã đến lúc chứng kiến ​​nó hoạt động. Bắt đầu mọi thứ bằng cách kích hoạt tác nhân bằng lệnh này:

```python
./run agent start SmartAgent.
```

Khi sân chơi kỹ thuật số của bạn đã được thiết lập xong, thiết bị đầu cuối của bạn sẽ sáng lên với:

```python



       d8888          888             .d8888b.  8888888b. 88888888888
      d88888          888            d88P  Y88b 888   Y88b    888
     d88P888          888            888    888 888    888    888
    d88P 888 888  888 888888 .d88b.  888        888   d88P    888
   d88P  888 888  888 888   d88""88b 888  88888 8888888P"     888
  d88P   888 888  888 888   888  888 888    888 888           888
 d8888888888 Y88b 888 Y88b. Y88..88P Y88b  d88P 888           888
d88P     888  "Y88888  "Y888 "Y88P"   "Y8888P88 888           888



                8888888888
                888
                888
                8888888  .d88b.  888d888 .d88b.   .d88b.
                888     d88""88b 888P"  d88P"88b d8P  Y8b
                888     888  888 888    888  888 88888888
                888     Y88..88P 888    Y88b 888 Y8b.
                888      "Y88P"  888     "Y88888  "Y8888
                                             888
                                        Y8b d88P
                                         "Y88P"                v0.1.0


[2023-09-27 15:39:07,832] [forge.sdk.agent] [INFO]      📝  Agent server starting on http://localhost:8000
```

Một cú nhấp chuột đơn giản vào liên kết đó sẽ hiển thị Giao diện người dùng AutoGPT Agent. Nhưng chờ đã, trước tiên có một điểm dừng nhỏ! Đăng nhập bằng thông tin đăng nhập Gmail hoặc Github của bạn. Bây giờ, bạn có thấy biểu tượng chiếc cúp ở bên trái không? Nhấp vào nó để bước vào đấu trường điểm chuẩn. Chọn tham gia thử nghiệm 'WriteFile' và nhấn 'Bắt ​​đầu bộ thử nghiệm' để bắt đầu chuyển động.

![](https://miro.medium.com/v2/resize:fit:1000/1*kGsn4AlU5nyXNIZpOF3eSQ.png)

Trang điểm chuẩn của giao diện người dùng AutoGPT

Mắt của bạn sẽ dán chặt vào bảng bên phải khi nó đưa ra kết quả theo thời gian thực. Và nếu bạn lén nhìn vào bảng điều khiển của mình, những thông báo ăn mừng này gợi ý rằng nhiệm vụ của bạn đã đạt đến phần cuối cùng:

```
📝  📦 Task created: 70518b75-0104-49b0-923e-f607719d042b input: Write the word 'Washington' to a .txt fi...
📝      ✅ Final Step completed: a736c45f-65a5-4c44-a697-f1d6dcd94d5c input: y
```

Ối! Gặp sự cố hoặc nhìn thấy một số thông báo lỗi khó hiểu? Nhạt toẹt. Nhấn thử lại. Hãy nhớ rằng, mặc dù LLM đóng vai trò là trí tuệ của đặc vụ, nhưng chúng hơi giống phù thủy — vô cùng mạnh mẽ nhưng đôi khi cần một cú huých nhẹ để đi đúng hướng!

Tóm lại
========

Trong hướng dẫn tiếp theo, chúng tôi sẽ cải tiến thêm quy trình này, nâng cao khả năng của tác nhân thông qua việc bổ sung bộ nhớ!

Cho đến lúc đó, hãy tiếp tục thử nghiệm và vượt qua các ranh giới của AI. Chúc mừng mã hóa! 🚀

<div style="text-align: right">Theo <a href="https://aiedge.medium.com/autogpt-forge-crafting-intelligent-agent-logic-bc5197b14cb4">Craig Swift</a></div>