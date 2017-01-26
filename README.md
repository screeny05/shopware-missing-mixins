# shopware-missing-mixins
[![license](https://img.shields.io/npm/l/shopware-missing-mixins.svg?style=flat-square)]()
[![npm](https://img.shields.io/npm/v/shopware-missing-mixins.svg?style=flat-square)]()
[![Bower](https://img.shields.io/bower/v/shopware-missing-mixins.svg?style=flat-square)]()

less-mixins to help you with your shopware-frontend

### how to use?
1. include all.less
2. adjust variables in your theme to your liking
3. ???
4. profit!

### what's included?
* various css-helpers
    * absolute-center
    * aspect-ratio
    * inline-block shorthand
    * line-through
    * on-active
    * position & size
    * text-overflow
    * hyphenation
* missing prefix-mixins
    * calc
    * filter
    * mask
    * placeholder
    * selection
    * column
* somewhat complete flex-mixins (IE 10+)
* for-mixin from [@seven-phases-max](https://github.com/seven-phases-max/less.curious)
* grid-mixins
* small icon utility
* path-mixins
* font-face-mixin
* media-query-mixins
* triangle-mixin
* emotion-grid-push (see below)

#### media-mixins
tired of typing `@media screen and (min-width: @phoneLandscapeViewportWidth)`?

look no further!

this library introduces the following new names for the breakpoints:
* `< 480px`: xs
* `480px  - 767px`: ms
* `768px  - 1023px`: sm
* `1024px - 1259px`: md
* `> 1259px`: lg

of course these are not harcoded but simply the default values shopware gives us via the [`structure.less`](https://github.com/shopware/shopware/blob/5.1/themes/Frontend/Responsive/frontend/_public/src/less/_variables/structure.less)-

with this naming and a few cool mixins you can write your media-queries like this:
```less
.product-box--title {
    padding-bottom: 10px;
    .screen-ms(padding-bottom, 20px);
    .screen-sm(padding-bottom, 30px);
    .screen-md({
        padding-bottom: 40px;
        margin-bottom: -10px;

        &.is--active {
            color: tomato;
        }

        .product-box--subtitle {
            background: rebeccapurple;
        }
    });
}
```
*of course i encourage you not to write code this messy*

resulting in css like this:
```css
.product-box--title {
    padding-bottom: 10px;
}

@media (min-width: 30em) {
    .product-box--title {
        padding-bottom: 20px;
    }
}

@media (min-width: 48em) {
    .product-box--title {
        padding-bottom: 20px;
    }
}

@media (min-width: 64em) {
    .product-box--title {
        padding-bottom: 20px;
        margin-bottom: -10px;
    }

    .product-box--title.is--active {
        color: tomato;
    }

    .product-box--title .product-box--subtitle {
        background: rebeccapurple;
    }
}
```

read more about the magical powers of less' detached rulesets in [the less docs](http://lesscss.org/features/#detached-rulesets-feature).


#### .create-emotion-grid-push
This mixin creates classes which you can add to your emotion-elements to fill the gutter between elements.

The mixin creates classes for removing the gutter to the right, to the left or on both sides.


### what's new?
* 0.4.0 - add `.create-emotion-grid-push` mixin
* 0.3.2 - fix relative paths for php less-compiler
* 0.3.1 - path now returns relative paths. fix for virtual paths
* 0.3.0 - add column mixins
* 0.2.0 - add hyphenation helper
* 0.1.2 - add property-value mixins for placeholder & selection
