The idea of this code is create a simple way to create animation classes.

@mixin animation($name, $animation) {
    @keyframes #{$name} {
        @content;
    }

    .#{$name} {
        animation: $name $animation;
    }
}

This mixin has 2 parameters: 
$name - name of class and animation-name value
$animation - animation parameters, except animation-name

We are using the conten of include for keyframes of animation.

-------------------------------------------
Example:

@include animation(animation-spin, 2s linear infinite){
    from { transform: rotate(0deg); }
    to { transform: rotate(359deg); }
};

Generated output:

@keyframes animation-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(359deg); }
}

.animation-spin {
    animation: animation-spin 2s linear infinite;
}

-------------------------------------------
Prefixes is not included, it can be managed with autoprefixer task 
https://www.npmjs.com/package/autoprefixer

You can find gulp/grunt autoprefixer module.