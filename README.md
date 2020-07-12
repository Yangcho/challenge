!function(A, e) {
    "use strict";
    "function" == typeof define && define.amd ? define([], e) : "object" == typeof module && module.exports ? module.exports = e() : (A.AnchorJS = e(),
    A.anchors = new A.AnchorJS)
}(this, function() {
    "use strict";
    function A(A) {
        function e(A) {
            A.icon = A.hasOwnProperty("icon") ? A.icon : "",
            A.visible = A.hasOwnProperty("visible") ? A.visible : "hover",
            A.placement = A.hasOwnProperty("placement") ? A.placement : "right",
            A.class = A.hasOwnProperty("class") ? A.class : "",
            A.truncate = A.hasOwnProperty("truncate") ? Math.floor(A.truncate) : 64
        }
        function t(A) {
            var e;
            if ("string" == typeof A || A instanceof String)
                e = [].slice.call(document.querySelectorAll(A));
            else {
                if (!(Array.isArray(A) || A instanceof NodeList))
                    throw new Error("The selector provided to AnchorJS was invalid.");
                e = [].slice.call(A)
            }
            return e
        }
        function n() {
            if (null === document.head.querySelector("style.anchorjs")) {
                var A, e = document.createElement("style");
                e.className = "anchorjs",
                e.appendChild(document.createTextNode("")),
                void 0 === (A = document.head.querySelector('[rel="stylesheet"], style')) ? document.head.appendChild(e) : document.head.insertBefore(e, A),
                e.sheet.insertRule(" .anchorjs-link {   opacity: 0;   text-decoration: none;   -webkit-font-smoothing: antialiased;   -moz-osx-font-smoothing: grayscale; }", e.sheet.cssRules.length),
                e.sheet.insertRule(" *:hover > .anchorjs-link, .anchorjs-link:focus  {   opacity: 1; }", e.sheet.cssRules.length),
                e.sheet.insertRule(" [data-anchorjs-icon]::after {   content: attr(data-anchorjs-icon); }", e.sheet.cssRules.length),
                e.sheet.insertRule(' @font-face {   font-family: "anchorjs-icons";   src: url(data:n/a;base64,AAEAAAALAIAAAwAwT1MvMg8yG2cAAAE4AAAAYGNtYXDp3gC3AAABpAAAAExnYXNwAAAAEAAAA9wAAAAIZ2x5ZlQCcfwAAAH4AAABCGhlYWQHFvHyAAAAvAAAADZoaGVhBnACFwAAAPQAAAAkaG10eASAADEAAAGYAAAADGxvY2EACACEAAAB8AAAAAhtYXhwAAYAVwAAARgAAAAgbmFtZQGOH9cAAAMAAAAAunBvc3QAAwAAAAADvAAAACAAAQAAAAEAAHzE2p9fDzz1AAkEAAAAAADRecUWAAAAANQA6R8AAAAAAoACwAAAAAgAAgAAAAAAAAABAAADwP/AAAACgAAA/9MCrQABAAAAAAAAAAAAAAAAAAAAAwABAAAAAwBVAAIAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAMCQAGQAAUAAAKZAswAAACPApkCzAAAAesAMwEJAAAAAAAAAAAAAAAAAAAAARAAAAAAAAAAAAAAAAAAAAAAQAAg//0DwP/AAEADwABAAAAAAQAAAAAAAAAAAAAAIAAAAAAAAAIAAAACgAAxAAAAAwAAAAMAAAAcAAEAAwAAABwAAwABAAAAHAAEADAAAAAIAAgAAgAAACDpy//9//8AAAAg6cv//f///+EWNwADAAEAAAAAAAAAAAAAAAAACACEAAEAAAAAAAAAAAAAAAAxAAACAAQARAKAAsAAKwBUAAABIiYnJjQ3NzY2MzIWFxYUBwcGIicmNDc3NjQnJiYjIgYHBwYUFxYUBwYGIwciJicmNDc3NjIXFhQHBwYUFxYWMzI2Nzc2NCcmNDc2MhcWFAcHBgYjARQGDAUtLXoWOR8fORYtLTgKGwoKCjgaGg0gEhIgDXoaGgkJBQwHdR85Fi0tOAobCgoKOBoaDSASEiANehoaCQkKGwotLXoWOR8BMwUFLYEuehYXFxYugC44CQkKGwo4GkoaDQ0NDXoaShoKGwoFBe8XFi6ALjgJCQobCjgaShoNDQ0NehpKGgobCgoKLYEuehYXAAAADACWAAEAAAAAAAEACAAAAAEAAAAAAAIAAwAIAAEAAAAAAAMACAAAAAEAAAAAAAQACAAAAAEAAAAAAAUAAQALAAEAAAAAAAYACAAAAAMAAQQJAAEAEAAMAAMAAQQJAAIABgAcAAMAAQQJAAMAEAAMAAMAAQQJAAQAEAAMAAMAAQQJAAUAAgAiAAMAAQQJAAYAEAAMYW5jaG9yanM0MDBAAGEAbgBjAGgAbwByAGoAcwA0ADAAMABAAAAAAwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABAAH//wAP) format("truetype"); }', e.sheet.cssRules.length)
            }
        }
        this.options = A || {},
        this.elements = [],
        e(this.options),
        this.isTouchDevice = function() {
            return !!("ontouchstart"in window || window.DocumentTouch && document instanceof DocumentTouch)
        }
        ,
        this.add = function(A) {
            var i, o, s, c, r, a, h, l, u, d, f, g, p = [];
            if (e(this.options),
            "touch" === (g = this.options.visible) && (g = this.isTouchDevice() ? "always" : "hover"),
            A || (A = "h2, h3, h4, h5, h6"),
            0 === (i = t(A)).length)
                return this;
            for (n(),
            o = document.querySelectorAll("[id]"),
            s = [].map.call(o, function(A) {
                return A.id
            }),
            r = 0; r < i.length; r++)
                if (this.hasAnchorJSLink(i[r]))
                    p.push(r);
                else {
                    if (i[r].hasAttribute("id"))
                        c = i[r].getAttribute("id");
                    else if (i[r].hasAttribute("data-anchor-id"))
                        c = i[r].getAttribute("data-anchor-id");
                    else {
                        u = l = this.urlify(i[r].textContent),
                        h = 0;
                        do {
                            void 0 !== a && (u = l + "-" + h),
                            a = s.indexOf(u),
                            h += 1
                        } while (-1 !== a);a = void 0,
                        s.push(u),
                        i[r].setAttribute("id", u),
                        c = u
                    }
                    d = c.replace(/-/g, " "),
                    (f = document.createElement("a")).className = "anchorjs-link " + this.options.class,
                    f.href = "#" + c,
                    f.setAttribute("aria-label", "Anchor link for: " + d),
                    f.setAttribute("data-anchorjs-icon", this.options.icon),
                    "always" === g && (f.style.opacity = "1"),
                    "" === this.options.icon && (f.style.font = "1em/1 anchorjs-icons",
                    "left" === this.options.placement && (f.style.lineHeight = "inherit")),
                    "left" === this.options.placement ? (f.style.position = "absolute",
                    f.style.marginLeft = "-1em",
                    f.style.paddingRight = "0.5em",
                    i[r].insertBefore(f, i[r].firstChild)) : (f.style.paddingLeft = "0.375em",
                    i[r].appendChild(f))
                }
            for (r = 0; r < p.length; r++)
                i.splice(p[r] - r, 1);
            return this.elements = this.elements.concat(i),
            this
        }
        ,
        this.remove = function(A) {
            for (var e, n, i = t(A), o = 0; o < i.length; o++)
                (n = i[o].querySelector(".anchorjs-link")) && (-1 !== (e = this.elements.indexOf(i[o])) && this.elements.splice(e, 1),
                i[o].removeChild(n));
            return this
        }
        ,
        this.removeAll = function() {
            this.remove(this.elements)
        }
        ,
        this.urlify = function(A) {
            var t = /[& +$,:;=?@"#{}|^~[`%!'<>\]\.\/\(\)\*\\]/g;
            return this.options.truncate || e(this.options),
            A.trim().replace(/\'/gi, "").replace(t, "-").replace(/-{2,}/g, "-").substring(0, this.options.truncate).replace(/^-+|-+$/gm, "").toLowerCase()
        }
        ,
        this.hasAnchorJSLink = function(A) {
            var e = A.firstChild && (" " + A.firstChild.className + " ").indexOf(" anchorjs-link ") > -1
              , t = A.lastChild && (" " + A.lastChild.className + " ").indexOf(" anchorjs-link ") > -1;
            return e || t || !1
        }
    }
    return A
});
