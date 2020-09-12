# Adding Mermaid Support in Hugo (Even Theme)


I tried some Hugo Themes, some are too powerful and complex to me, such as Academic. I did some research and find Even is a suitable theme to me: easy to set up, float TOC, some minor modification to support Mermaid. Here we go! 

<!-- more -->

## Steps

1. add code below in `yoursite/themes/themes_name/layouts/partials/footer.html`

```html
<script src="https://cdn.bootcss.com/mermaid/8.8.0/mermaid.min.js"></script>
```
2.  Create `mermaid.html` under `shortcodes`

```html
<div class="mermaid" align="{{ if .Get "align" }}
                                {{ .Get "align" }}
                            {{ else }} 
                                center
                            {{ end }}"> 
    {{ safeHTML .Inner }}
</div>
```

3. Test

```

graph LR
A(interview)-->B(exam)
A-->C(interview)
C-->C1(data structure and algorithm)
C-->C2(computer network)
C-->C3(operating system - Linux)
B-->B1(data structure and algorithm)

```

>start with \{\{\<mermaid\>\}\}  
>end with \{\{\<\/mermaid\>\}\}

{{<mermaid>}}
graph LR
A(interview)-->B(exam)
A-->C(interview)
C-->C1(data structure and algorithm)
C-->C2(computer network)
C-->C3(operating system - Linux)
B-->B1(data structure and algorithm)
{{</mermaid>}}

---

## Reference


[[转载]在hugo中添加mermaid支持](https://chrishrz.github.io/post/%E8%BD%AC%E8%BD%BD%E5%9C%A8hugo%E4%B8%AD%E6%B7%BB%E5%8A%A0mermaid%E6%94%AF%E6%8C%81/)
[拓展hugo的markdown_流程图mermaid](https://kentxxq.com/contents/拓展hugo的markdown_流程图mermaid/)
