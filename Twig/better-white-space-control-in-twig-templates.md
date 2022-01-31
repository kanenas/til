# Better White Space Control in Twig Templates

Whitespace control in Twig templates allows you to control the indentation and spacing of the generated contents (usually HTML code).  
**Read more**: https://symfony.com/blog/better-white-space-control-in-twig-templates

**BEFORE**  
```
<ul>
    <li>
        {% if some_expression %}
            {{ some_variable }}
        {% endif %}
    </li>
</ul>
```
```
<ul>
    <li>
            Lorem Ipsum
        </li>
</ul>
```

**AFTER**  
```
<ul>
    <li>
        {%- if some_expression %}
            {{- some_variable -}}
        {% endif -%}
    </li>
</ul>
```
```
<ul>
    <li>Lorem Ipsum</li>
</ul>
```
