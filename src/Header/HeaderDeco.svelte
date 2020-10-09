<script>
    // your script goes here
</script>

<style type="text/scss">
    /* your styles go here */

    $resolution-tablet: 768px;
    $resolution-desktop: 998px;

    
    @mixin for-size($size){
        @if $size == tablet {
            @media (min-width: #{$resolution-tablet}) {@content;}
        } @else if $size == desktop {
            @media (min-width: #{$resolution-desktop}) {@content;}
        } @else if $size == smallerThanTablet {
            @media (max-width: #{$resolution-tablet}) {@content;}
        } @else if $size == smallerThanDesktop {
            @media (max-width: #{$resolution-desktop}) {@content;}
        }
    }

    $green-cream: #C1DFC4;
    $orange: #EA5B0C;

    $thirdBubbleSize:14.5%;

    .header__deco{
        max-width: 400px;
        padding: 1rem;
        box-sizing: border-box;
        position: absolute;
        bottom: -180px;
        right: 0;

        &:after{
            content: '';
            display: inline-block;
            height: $thirdBubbleSize;
            width: $thirdBubbleSize;
            background-color: $orange;
            border-radius: 100%;
            position: absolute;
            top: 50%;
            right: 0;
        }

        @include for-size(desktop){
            width: 50%;
            max-width: 700px;
        }
    }

    .imgBubble{
        max-width: 100%;
    }

    .imgBubble--main{}

    .imgBubble--secondary{
        position: absolute;
        top: 50%;
        left: -16%;
        //height: 32%;
        width: 32%;
    }
</style>

<!-- markup (zero or more items) goes here -->

<div class="header__deco">
    <img src="asset/img/party01.png" class="imgBubble imgBubble--main"/>
    <img src="asset/img/party02.png" class="imgBubble imgBubble--secondary"/>
</div>