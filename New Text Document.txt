var e = Object.create
  , t = Object.defineProperty
  , n = Object.getOwnPropertyDescriptor
  , r = Object.getOwnPropertyNames
  , i = Object.getPrototypeOf
  , a = Object.prototype.hasOwnProperty
  , o = (e, t) => () => (t || e((t = {
    exports: {}
}).exports, t),
t.exports)
  , s = (e, n) => {
    let r = {};
    for (var i in e)
        t(r, i, {
            get: e[i],
            enumerable: !0
        });
    return n || t(r, Symbol.toStringTag, {
        value: `Module`
    }),
    r
}
  , c = (e, i, o, s) => {
    if (i && typeof i == `object` || typeof i == `function`)
        for (var c = r(i), l = 0, u = c.length, d; l < u; l++)
            d = c[l],
            !a.call(e, d) && d !== o && t(e, d, {
                get: (e => i[e]).bind(null, d),
                enumerable: !(s = n(i, d)) || s.enumerable
            });
    return e
}
  , l = (n, r, a) => (a = n == null ? {} : e(i(n)),
c(r || !n || !n.__esModule ? t(a, `default`, {
    value: n,
    enumerable: !0
}) : a, n))
  , u = `modulepreload`
  , d = function(e) {
    return `/preview/6970c675-1c7b-4278-b8c2-58ef29f9255b/7705266/` + e
}
  , f = {}
  , p = function(e, t, n) {
    let r = Promise.resolve();
    if (t && t.length > 0) {
        let e = document.getElementsByTagName(`link`)
          , i = document.querySelector(`meta[property=csp-nonce]`)
          , a = i?.nonce || i?.getAttribute(`nonce`);
        function o(e) {
            return Promise.all(e.map(e => Promise.resolve(e).then(e => ({
                status: `fulfilled`,
                value: e
            }), e => ({
                status: `rejected`,
                reason: e
            }))))
        }
        r = o(t.map(t => {
            if (t = d(t, n),
            t in f)
                return;
            f[t] = !0;
            let r = t.endsWith(`.css`)
              , i = r ? `[rel="stylesheet"]` : ``;
            if (n)
                for (let n = e.length - 1; n >= 0; n--) {
                    let i = e[n];
                    if (i.href === t && (!r || i.rel === `stylesheet`))
                        return
                }
            else if (document.querySelector(`link[href="${t}"]${i}`))
                return;
            let o = document.createElement(`link`);
            if (o.rel = r ? `stylesheet` : u,
            r || (o.as = `script`),
            o.crossOrigin = ``,
            o.href = t,
            a && o.setAttribute(`nonce`, a),
            document.head.appendChild(o),
            r)
                return new Promise( (e, n) => {
                    o.addEventListener(`load`, e),
                    o.addEventListener(`error`, () => n(Error(`Unable to preload CSS for ${t}`)))
                }
                )
        }
        ))
    }
    function i(e) {
        let t = new Event(`vite:preloadError`,{
            cancelable: !0
        });
        if (t.payload = e,
        window.dispatchEvent(t),
        !t.defaultPrevented)
            throw e
    }
    return r.then(t => {
        for (let e of t || [])
            e.status === `rejected` && i(e.reason);
        return e().catch(i)
    }
    )
}
  , m = o((e => {
    var t = Symbol.for(`react.transitional.element`)
      , n = Symbol.for(`react.portal`)
      , r = Symbol.for(`react.fragment`)
      , i = Symbol.for(`react.strict_mode`)
      , a = Symbol.for(`react.profiler`)
      , o = Symbol.for(`react.consumer`)
      , s = Symbol.for(`react.context`)
      , c = Symbol.for(`react.forward_ref`)
      , l = Symbol.for(`react.suspense`)
      , u = Symbol.for(`react.memo`)
      , d = Symbol.for(`react.lazy`)
      , f = Symbol.for(`react.activity`)
      , p = Symbol.iterator;
    function m(e) {
        return typeof e != `object` || !e ? null : (e = p && e[p] || e[`@@iterator`],
        typeof e == `function` ? e : null)
    }
    var h = {
        isMounted: function() {
            return !1
        },
        enqueueForceUpdate: function() {},
        enqueueReplaceState: function() {},
        enqueueSetState: function() {}
    }
      , g = Object.assign
      , _ = {};
    function v(e, t, n) {
        this.props = e,
        this.context = t,
        this.refs = _,
        this.updater = n || h
    }
    v.prototype.isReactComponent = {},
    v.prototype.setState = function(e, t) {
        if (typeof e != `object` && typeof e != `function` && e != null)
            throw Error(`takes an object of state variables to update or a function which returns an object of state variables.`);
        this.updater.enqueueSetState(this, e, t, `setState`)
    }
    ,
    v.prototype.forceUpdate = function(e) {
        this.updater.enqueueForceUpdate(this, e, `forceUpdate`)
    }
    ;
    function y() {}
    y.prototype = v.prototype;
    function b(e, t, n) {
        this.props = e,
        this.context = t,
        this.refs = _,
        this.updater = n || h
    }
    var x = b.prototype = new y;
    x.constructor = b,
    g(x, v.prototype),
    x.isPureReactComponent = !0;
    var S = Array.isArray;
    function C() {}
    var w = {
        H: null,
        A: null,
        T: null,
        S: null
    }
      , T = Object.prototype.hasOwnProperty;
    function E(e, n, r) {
        var i = r.ref;
        return {
            $$typeof: t,
            type: e,
            key: n,
            ref: i === void 0 ? null : i,
            props: r
        }
    }
    function D(e, t) {
        return E(e.type, t, e.props)
    }
    function O(e) {
        return typeof e == `object` && !!e && e.$$typeof === t
    }
    function k(e) {
        var t = {
            "=": `=0`,
            ":": `=2`
        };
        return `$` + e.replace(/[=:]/g, function(e) {
            return t[e]
        })
    }
    var A = /\/+/g;
    function j(e, t) {
        return typeof e == `object` && e && e.key != null ? k(`` + e.key) : t.toString(36)
    }
    function ee(e) {
        switch (e.status) {
        case `fulfilled`:
            return e.value;
        case `rejected`:
            throw e.reason;
        default:
            switch (typeof e.status == `string` ? e.then(C, C) : (e.status = `pending`,
            e.then(function(t) {
                e.status === `pending` && (e.status = `fulfilled`,
                e.value = t)
            }, function(t) {
                e.status === `pending` && (e.status = `rejected`,
                e.reason = t)
            })),
            e.status) {
            case `fulfilled`:
                return e.value;
            case `rejected`:
                throw e.reason
            }
        }
        throw e
    }
    function M(e, r, i, a, o) {
        var s = typeof e;
        (s === `undefined` || s === `boolean`) && (e = null);
        var c = !1;
        if (e === null)
            c = !0;
        else
            switch (s) {
            case `bigint`:
            case `string`:
            case `number`:
                c = !0;
                break;
            case `object`:
                switch (e.$$typeof) {
                case t:
                case n:
                    c = !0;
                    break;
                case d:
                    return c = e._init,
                    M(c(e._payload), r, i, a, o)
                }
            }
        if (c)
            return o = o(e),
            c = a === `` ? `.` + j(e, 0) : a,
            S(o) ? (i = ``,
            c != null && (i = c.replace(A, `$&/`) + `/`),
            M(o, r, i, ``, function(e) {
                return e
            })) : o != null && (O(o) && (o = D(o, i + (o.key == null || e && e.key === o.key ? `` : (`` + o.key).replace(A, `$&/`) + `/`) + c)),
            r.push(o)),
            1;
        c = 0;
        var l = a === `` ? `.` : a + `:`;
        if (S(e))
            for (var u = 0; u < e.length; u++)
                a = e[u],
                s = l + j(a, u),
                c += M(a, r, i, s, o);
        else if (u = m(e),
        typeof u == `function`)
            for (e = u.call(e),
            u = 0; !(a = e.next()).done; )
                a = a.value,
                s = l + j(a, u++),
                c += M(a, r, i, s, o);
        else if (s === `object`) {
            if (typeof e.then == `function`)
                return M(ee(e), r, i, a, o);
            throw r = String(e),
            Error(`Objects are not valid as a React child (found: ` + (r === `[object Object]` ? `object with keys {` + Object.keys(e).join(`, `) + `}` : r) + `). If you meant to render a collection of children, use an array instead.`)
        }
        return c
    }
    function N(e, t, n) {
        if (e == null)
            return e;
        var r = []
          , i = 0;
        return M(e, r, ``, ``, function(e) {
            return t.call(n, e, i++)
        }),
        r
    }
    function te(e) {
        if (e._status === -1) {
            var t = e._result;
            t = t(),
            t.then(function(t) {
                (e._status === 0 || e._status === -1) && (e._status = 1,
                e._result = t)
            }, function(t) {
                (e._status === 0 || e._status === -1) && (e._status = 2,
                e._result = t)
            }),
            e._status === -1 && (e._status = 0,
            e._result = t)
        }
        if (e._status === 1)
            return e._result.default;
        throw e._result
    }
    var ne = typeof reportError == `function` ? reportError : function(e) {
        if (typeof window == `object` && typeof window.ErrorEvent == `function`) {
            var t = new window.ErrorEvent(`error`,{
                bubbles: !0,
                cancelable: !0,
                message: typeof e == `object` && e && typeof e.message == `string` ? String(e.message) : String(e),
                error: e
            });
            if (!window.dispatchEvent(t))
                return
        } else if (typeof process == `object` && typeof process.emit == `function`) {
            process.emit(`uncaughtException`, e);
            return
        }
        console.error(e)
    }
      , re = {
        map: N,
        forEach: function(e, t, n) {
            N(e, function() {
                t.apply(this, arguments)
            }, n)
        },
        count: function(e) {
            var t = 0;
            return N(e, function() {
                t++
            }),
            t
        },
        toArray: function(e) {
            return N(e, function(e) {
                return e
            }) || []
        },
        only: function(e) {
            if (!O(e))
                throw Error(`React.Children.only expected to receive a single React element child.`);
            return e
        }
    };
    e.Activity = f,
    e.Children = re,
    e.Component = v,
    e.Fragment = r,
    e.Profiler = a,
    e.PureComponent = b,
    e.StrictMode = i,
    e.Suspense = l,
    e.__CLIENT_INTERNALS_DO_NOT_USE_OR_WARN_USERS_THEY_CANNOT_UPGRADE = w,
    e.__COMPILER_RUNTIME = {
        __proto__: null,
        c: function(e) {
            return w.H.useMemoCache(e)
        }
    },
    e.cache = function(e) {
        return function() {
            return e.apply(null, arguments)
        }
    }
    ,
    e.cacheSignal = function() {
        return null
    }
    ,
    e.cloneElement = function(e, t, n) {
        if (e == null)
            throw Error(`The argument must be a React element, but you passed ` + e + `.`);
        var r = g({}, e.props)
          , i = e.key;
        if (t != null)
            for (a in t.key !== void 0 && (i = `` + t.key),
            t)
                !T.call(t, a) || a === `key` || a === `__self` || a === `__source` || a === `ref` && t.ref === void 0 || (r[a] = t[a]);
        var a = arguments.length - 2;
        if (a === 1)
            r.children = n;
        else if (1 < a) {
            for (var o = Array(a), s = 0; s < a; s++)
                o[s] = arguments[s + 2];
            r.children = o
        }
        return E(e.type, i, r)
    }
    ,
    e.createContext = function(e) {
        return e = {
            $$typeof: s,
            _currentValue: e,
            _currentValue2: e,
            _threadCount: 0,
            Provider: null,
            Consumer: null
        },
        e.Provider = e,
        e.Consumer = {
            $$typeof: o,
            _context: e
        },
        e
    }
    ,
    e.createElement = function(e, t, n) {
        var r, i = {}, a = null;
        if (t != null)
            for (r in t.key !== void 0 && (a = `` + t.key),
            t)
                T.call(t, r) && r !== `key` && r !== `__self` && r !== `__source` && (i[r] = t[r]);
        var o = arguments.length - 2;
        if (o === 1)
            i.children = n;
        else if (1 < o) {
            for (var s = Array(o), c = 0; c < o; c++)
                s[c] = arguments[c + 2];
            i.children = s
        }
        if (e && e.defaultProps)
            for (r in o = e.defaultProps,
            o)
                i[r] === void 0 && (i[r] = o[r]);
        return E(e, a, i)
    }
    ,
    e.createRef = function() {
        return {
            current: null
        }
    }
    ,
    e.forwardRef = function(e) {
        return {
            $$typeof: c,
            render: e
        }
    }
    ,
    e.isValidElement = O,
    e.lazy = function(e) {
        return {
            $$typeof: d,
            _payload: {
                _status: -1,
                _result: e
            },
            _init: te
        }
    }
    ,
    e.memo = function(e, t) {
        return {
            $$typeof: u,
            type: e,
            compare: t === void 0 ? null : t
        }
    }
    ,
    e.startTransition = function(e) {
        var t = w.T
          , n = {};
        w.T = n;
        try {
            var r = e()
              , i = w.S;
            i !== null && i(n, r),
            typeof r == `object` && r && typeof r.then == `function` && r.then(C, ne)
        } catch (e) {
            ne(e)
        } finally {
            t !== null && n.types !== null && (t.types = n.types),
            w.T = t
        }
    }
    ,
    e.unstable_useCacheRefresh = function() {
        return w.H.useCacheRefresh()
    }
    ,
    e.use = function(e) {
        return w.H.use(e)
    }
    ,
    e.useActionState = function(e, t, n) {
        return w.H.useActionState(e, t, n)
    }
    ,
    e.useCallback = function(e, t) {
        return w.H.useCallback(e, t)
    }
    ,
    e.useContext = function(e) {
        return w.H.useContext(e)
    }
    ,
    e.useDebugValue = function() {}
    ,
    e.useDeferredValue = function(e, t) {
        return w.H.useDeferredValue(e, t)
    }
    ,
    e.useEffect = function(e, t) {
        return w.H.useEffect(e, t)
    }
    ,
    e.useEffectEvent = function(e) {
        return w.H.useEffectEvent(e)
    }
    ,
    e.useId = function() {
        return w.H.useId()
    }
    ,
    e.useImperativeHandle = function(e, t, n) {
        return w.H.useImperativeHandle(e, t, n)
    }
    ,
    e.useInsertionEffect = function(e, t) {
        return w.H.useInsertionEffect(e, t)
    }
    ,
    e.useLayoutEffect = function(e, t) {
        return w.H.useLayoutEffect(e, t)
    }
    ,
    e.useMemo = function(e, t) {
        return w.H.useMemo(e, t)
    }
    ,
    e.useOptimistic = function(e, t) {
        return w.H.useOptimistic(e, t)
    }
    ,
    e.useReducer = function(e, t, n) {
        return w.H.useReducer(e, t, n)
    }
    ,
    e.useRef = function(e) {
        return w.H.useRef(e)
    }
    ,
    e.useState = function(e) {
        return w.H.useState(e)
    }
    ,
    e.useSyncExternalStore = function(e, t, n) {
        return w.H.useSyncExternalStore(e, t, n)
    }
    ,
    e.useTransition = function() {
        return w.H.useTransition()
    }
    ,
    e.version = `19.2.4`
}
))
  , h = o(( (e, t) => {
    t.exports = m()
}
))
  , g = o((e => {
    var t = Symbol.for(`react.transitional.element`)
      , n = Symbol.for(`react.fragment`);
    function r(e, n, r) {
        var i = null;
        if (r !== void 0 && (i = `` + r),
        n.key !== void 0 && (i = `` + n.key),
        `key`in n)
            for (var a in r = {},
            n)
                a !== `key` && (r[a] = n[a]);
        else
            r = n;
        return n = r.ref,
        {
            $$typeof: t,
            type: e,
            key: i,
            ref: n === void 0 ? null : n,
            props: r
        }
    }
    e.Fragment = n,
    e.jsx = r,
    e.jsxs = r
}
))
  , _ = o(( (e, t) => {
    t.exports = g()
}
))
  , v = l(h(), 1)
  , y = `popstate`;
function b(e) {
    return typeof e == `object` && !!e && `pathname`in e && `search`in e && `hash`in e && `state`in e && `key`in e
}
function x(e={}) {
    function t(e, t) {
        let n = t.state?.masked
          , {pathname: r, search: i, hash: a} = n || e.location;
        return E(``, {
            pathname: r,
            search: i,
            hash: a
        }, t.state && t.state.usr || null, t.state && t.state.key || `default`, n ? {
            pathname: e.location.pathname,
            search: e.location.search,
            hash: e.location.hash
        } : void 0)
    }
    function n(e, t) {
        return typeof t == `string` ? t : D(t)
    }
    return k(t, n, null, e)
}
function S(e, t) {
    if (e === !1 || e == null)
        throw Error(t)
}
function C(e, t) {
    if (!e) {
        typeof console < `u` && console.warn(t);
        try {
            throw Error(t)
        } catch {}
    }
}
function w() {
    return Math.random().toString(36).substring(2, 10)
}
function T(e, t) {
    return {
        usr: e.state,
        key: e.key,
        idx: t,
        masked: e.unstable_mask ? {
            pathname: e.pathname,
            search: e.search,
            hash: e.hash
        } : void 0
    }
}
function E(e, t, n=null, r, i) {
    return {
        pathname: typeof e == `string` ? e : e.pathname,
        search: ``,
        hash: ``,
        ...typeof t == `string` ? O(t) : t,
        state: n,
        key: t && t.key || r || w(),
        unstable_mask: i
    }
}
function D({pathname: e=`/`, search: t=``, hash: n=``}) {
    return t && t !== `?` && (e += t.charAt(0) === `?` ? t : `?` + t),
    n && n !== `#` && (e += n.charAt(0) === `#` ? n : `#` + n),
    e
}
function O(e) {
    let t = {};
    if (e) {
        let n = e.indexOf(`#`);
        n >= 0 && (t.hash = e.substring(n),
        e = e.substring(0, n));
        let r = e.indexOf(`?`);
        r >= 0 && (t.search = e.substring(r),
        e = e.substring(0, r)),
        e && (t.pathname = e)
    }
    return t
}
function k(e, t, n, r={}) {
    let {window: i=document.defaultView, v5Compat: a=!1} = r
      , o = i.history
      , s = `POP`
      , c = null
      , l = u();
    l ?? (l = 0,
    o.replaceState({
        ...o.state,
        idx: l
    }, ``));
    function u() {
        return (o.state || {
            idx: null
        }).idx
    }
    function d() {
        s = `POP`;
        let e = u()
          , t = e == null ? null : e - l;
        l = e,
        c && c({
            action: s,
            location: h.location,
            delta: t
        })
    }
    function f(e, t) {
        s = `PUSH`;
        let r = b(e) ? e : E(h.location, e, t);
        n && n(r, e),
        l = u() + 1;
        let d = T(r, l)
          , f = h.createHref(r.unstable_mask || r);
        try {
            o.pushState(d, ``, f)
        } catch (e) {
            if (e instanceof DOMException && e.name === `DataCloneError`)
                throw e;
            i.location.assign(f)
        }
        a && c && c({
            action: s,
            location: h.location,
            delta: 1
        })
    }
    function p(e, t) {
        s = `REPLACE`;
        let r = b(e) ? e : E(h.location, e, t);
        n && n(r, e),
        l = u();
        let i = T(r, l)
          , d = h.createHref(r.unstable_mask || r);
        o.replaceState(i, ``, d),
        a && c && c({
            action: s,
            location: h.location,
            delta: 0
        })
    }
    function m(e) {
        return A(e)
    }
    let h = {
        get action() {
            return s
        },
        get location() {
            return e(i, o)
        },
        listen(e) {
            if (c)
                throw Error(`A history only accepts one active listener`);
            return i.addEventListener(y, d),
            c = e,
            () => {
                i.removeEventListener(y, d),
                c = null
            }
        },
        createHref(e) {
            return t(i, e)
        },
        createURL: m,
        encodeLocation(e) {
            let t = m(e);
            return {
                pathname: t.pathname,
                search: t.search,
                hash: t.hash
            }
        },
        push: f,
        replace: p,
        go(e) {
            return o.go(e)
        }
    };
    return h
}
function A(e, t=!1) {
    let n = `http://localhost`;
    typeof window < `u` && (n = window.location.origin === `null` ? window.location.href : window.location.origin),
    S(n, `No window.location.(origin|href) available to create URL`);
    let r = typeof e == `string` ? e : D(e);
    return r = r.replace(/ $/, `%20`),
    !t && r.startsWith(`//`) && (r = n + r),
    new URL(r,n)
}
function j(e, t, n=`/`) {
    return ee(e, t, n, !1)
}
function ee(e, t, n, r) {
    let i = F((typeof t == `string` ? O(t) : t).pathname || `/`, n);
    if (i == null)
        return null;
    let a = N(e);
    ne(a);
    let o = null;
    for (let e = 0; o == null && e < a.length; ++e) {
        let t = me(i);
        o = fe(a[e], t, r)
    }
    return o
}
function M(e, t) {
    let {route: n, pathname: r, params: i} = e;
    return {
        id: n.id,
        pathname: r,
        params: i,
        data: t[n.id],
        loaderData: t[n.id],
        handle: n.handle
    }
}
function N(e, t=[], n=[], r=``, i=!1) {
    let a = (e, a, o=i, s) => {
        let c = {
            relativePath: s === void 0 ? e.path || `` : s,
            caseSensitive: e.caseSensitive === !0,
            childrenIndex: a,
            route: e
        };
        if (c.relativePath.startsWith(`/`)) {
            if (!c.relativePath.startsWith(r) && o)
                return;
            S(c.relativePath.startsWith(r), `Absolute route path "${c.relativePath}" nested under path "${r}" is not valid. An absolute child route path must start with the combined path of all its parent routes.`),
            c.relativePath = c.relativePath.slice(r.length)
        }
        let l = I([r, c.relativePath])
          , u = n.concat(c);
        e.children && e.children.length > 0 && (S(e.index !== !0, `Index routes must not have child routes. Please remove all child routes from route path "${l}".`),
        N(e.children, t, u, l, o)),
        !(e.path == null && !e.index) && t.push({
            path: l,
            score: ue(l, e.index),
            routesMeta: u
        })
    }
    ;
    return e.forEach( (e, t) => {
        if (e.path === `` || !e.path?.includes(`?`))
            a(e, t);
        else
            for (let n of te(e.path))
                a(e, t, !0, n)
    }
    ),
    t
}
function te(e) {
    let t = e.split(`/`);
    if (t.length === 0)
        return [];
    let[n,...r] = t
      , i = n.endsWith(`?`)
      , a = n.replace(/\?$/, ``);
    if (r.length === 0)
        return i ? [a, ``] : [a];
    let o = te(r.join(`/`))
      , s = [];
    return s.push(...o.map(e => e === `` ? a : [a, e].join(`/`))),
    i && s.push(...o),
    s.map(t => e.startsWith(`/`) && t === `` ? `/` : t)
}
function ne(e) {
    e.sort( (e, t) => e.score === t.score ? de(e.routesMeta.map(e => e.childrenIndex), t.routesMeta.map(e => e.childrenIndex)) : t.score - e.score)
}
var re = /^:[\w-]+$/
  , ie = 3
  , ae = 2
  , oe = 1
  , se = 10
  , ce = -2
  , le = e => e === `*`;
function ue(e, t) {
    let n = e.split(`/`)
      , r = n.length;
    return n.some(le) && (r += ce),
    t && (r += ae),
    n.filter(e => !le(e)).reduce( (e, t) => e + (re.test(t) ? ie : t === `` ? oe : se), r)
}
function de(e, t) {
    return e.length === t.length && e.slice(0, -1).every( (e, n) => e === t[n]) ? e[e.length - 1] - t[t.length - 1] : 0
}
function fe(e, t, n=!1) {
    let {routesMeta: r} = e
      , i = {}
      , a = `/`
      , o = [];
    for (let e = 0; e < r.length; ++e) {
        let s = r[e]
          , c = e === r.length - 1
          , l = a === `/` ? t : t.slice(a.length) || `/`
          , u = P({
            path: s.relativePath,
            caseSensitive: s.caseSensitive,
            end: c
        }, l)
          , d = s.route;
        if (!u && c && n && !r[r.length - 1].route.index && (u = P({
            path: s.relativePath,
            caseSensitive: s.caseSensitive,
            end: !1
        }, l)),
        !u)
            return null;
        Object.assign(i, u.params),
        o.push({
            params: i,
            pathname: I([a, u.pathname]),
            pathnameBase: Se(I([a, u.pathnameBase])),
            route: d
        }),
        u.pathnameBase !== `/` && (a = I([a, u.pathnameBase]))
    }
    return o
}
function P(e, t) {
    typeof e == `string` && (e = {
        path: e,
        caseSensitive: !1,
        end: !0
    });
    let[n,r] = pe(e.path, e.caseSensitive, e.end)
      , i = t.match(n);
    if (!i)
        return null;
    let a = i[0]
      , o = a.replace(/(.)\/+$/, `$1`)
      , s = i.slice(1);
    return {
        params: r.reduce( (e, {paramName: t, isOptional: n}, r) => {
            if (t === `*`) {
                let e = s[r] || ``;
                o = a.slice(0, a.length - e.length).replace(/(.)\/+$/, `$1`)
            }
            let i = s[r];
            return n && !i ? e[t] = void 0 : e[t] = (i || ``).replace(/%2F/g, `/`),
            e
        }
        , {}),
        pathname: a,
        pathnameBase: o,
        pattern: e
    }
}
function pe(e, t=!1, n=!0) {
    C(e === `*` || !e.endsWith(`*`) || e.endsWith(`/*`), `Route path "${e}" will be treated as if it were "${e.replace(/\*$/, `/*`)}" because the \`*\` character must always follow a \`/\` in the pattern. To get rid of this warning, please change the route path to "${e.replace(/\*$/, `/*`)}".`);
    let r = []
      , i = `^` + e.replace(/\/*\*?$/, ``).replace(/^\/*/, `/`).replace(/[\\.*+^${}|()[\]]/g, `\\$&`).replace(/\/:([\w-]+)(\?)?/g, (e, t, n, i, a) => {
        if (r.push({
            paramName: t,
            isOptional: n != null
        }),
        n) {
            let t = a.charAt(i + e.length);
            return t && t !== `/` ? `/([^\\/]*)` : `(?:/([^\\/]*))?`
        }
        return `/([^\\/]+)`
    }
    ).replace(/\/([\w-]+)\?(\/|$)/g, `(/$1)?$2`);
    return e.endsWith(`*`) ? (r.push({
        paramName: `*`
    }),
    i += e === `*` || e === `/*` ? `(.*)$` : `(?:\\/(.+)|\\/*)$`) : n ? i += `\\/*$` : e !== `` && e !== `/` && (i += `(?:(?=\\/|$))`),
    [new RegExp(i,t ? void 0 : `i`), r]
}
function me(e) {
    try {
        return e.split(`/`).map(e => decodeURIComponent(e).replace(/\//g, `%2F`)).join(`/`)
    } catch (t) {
        return C(!1, `The URL path "${e}" could not be decoded because it is a malformed URL segment. This is probably due to a bad percent encoding (${t}).`),
        e
    }
}
function F(e, t) {
    if (t === `/`)
        return e;
    if (!e.toLowerCase().startsWith(t.toLowerCase()))
        return null;
    let n = t.endsWith(`/`) ? t.length - 1 : t.length
      , r = e.charAt(n);
    return r && r !== `/` ? null : e.slice(n) || `/`
}
var he = /^(?:[a-z][a-z0-9+.-]*:|\/\/)/i;
function ge(e, t=`/`) {
    let {pathname: n, search: r=``, hash: i=``} = typeof e == `string` ? O(e) : e, a;
    return n ? (n = n.replace(/\/\/+/g, `/`),
    a = n.startsWith(`/`) ? _e(n.substring(1), `/`) : _e(n, t)) : a = t,
    {
        pathname: a,
        search: Ce(r),
        hash: we(i)
    }
}
function _e(e, t) {
    let n = t.replace(/\/+$/, ``).split(`/`);
    return e.split(`/`).forEach(e => {
        e === `..` ? n.length > 1 && n.pop() : e !== `.` && n.push(e)
    }
    ),
    n.length > 1 ? n.join(`/`) : `/`
}
function ve(e, t, n, r) {
    return `Cannot include a '${e}' character in a manually specified \`to.${t}\` field [${JSON.stringify(r)}].  Please separate it out to the \`to.${n}\` field. Alternatively you may provide the full path as a string in <Link to="..."> and the router will parse it for you.`
}
function ye(e) {
    return e.filter( (e, t) => t === 0 || e.route.path && e.route.path.length > 0)
}
function be(e) {
    let t = ye(e);
    return t.map( (e, n) => n === t.length - 1 ? e.pathname : e.pathnameBase)
}
function xe(e, t, n, r=!1) {
    let i;
    typeof e == `string` ? i = O(e) : (i = {
        ...e
    },
    S(!i.pathname || !i.pathname.includes(`?`), ve(`?`, `pathname`, `search`, i)),
    S(!i.pathname || !i.pathname.includes(`#`), ve(`#`, `pathname`, `hash`, i)),
    S(!i.search || !i.search.includes(`#`), ve(`#`, `search`, `hash`, i)));
    let a = e === `` || i.pathname === ``, o = a ? `/` : i.pathname, s;
    if (o == null)
        s = n;
    else {
        let e = t.length - 1;
        if (!r && o.startsWith(`..`)) {
            let t = o.split(`/`);
            for (; t[0] === `..`; )
                t.shift(),
                --e;
            i.pathname = t.join(`/`)
        }
        s = e >= 0 ? t[e] : `/`
    }
    let c = ge(i, s)
      , l = o && o !== `/` && o.endsWith(`/`)
      , u = (a || o === `.`) && n.endsWith(`/`);
    return !c.pathname.endsWith(`/`) && (l || u) && (c.pathname += `/`),
    c
}
var I = e => e.join(`/`).replace(/\/\/+/g, `/`)
  , Se = e => e.replace(/\/+$/, ``).replace(/^\/*/, `/`)
  , Ce = e => !e || e === `?` ? `` : e.startsWith(`?`) ? e : `?` + e
  , we = e => !e || e === `#` ? `` : e.startsWith(`#`) ? e : `#` + e
  , Te = class {
    constructor(e, t, n, r=!1) {
        this.status = e,
        this.statusText = t || ``,
        this.internal = r,
        n instanceof Error ? (this.data = n.toString(),
        this.error = n) : this.data = n
    }
}
;
function Ee(e) {
    return e != null && typeof e.status == `number` && typeof e.statusText == `string` && typeof e.internal == `boolean` && `data`in e
}
function De(e) {
    return e.map(e => e.route.path).filter(Boolean).join(`/`).replace(/\/\/*/g, `/`) || `/`
}
var Oe = typeof window < `u` && window.document !== void 0 && window.document.createElement !== void 0;
function ke(e, t) {
    let n = e;
    if (typeof n != `string` || !he.test(n))
        return {
            absoluteURL: void 0,
            isExternal: !1,
            to: n
        };
    let r = n
      , i = !1;
    if (Oe)
        try {
            let e = new URL(window.location.href)
              , r = n.startsWith(`//`) ? new URL(e.protocol + n) : new URL(n)
              , a = F(r.pathname, t);
            r.origin === e.origin && a != null ? n = a + r.search + r.hash : i = !0
        } catch {
            C(!1, `<Link to="${n}"> contains an invalid URL which will probably break when clicked - please update to a valid URL path.`)
        }
    return {
        absoluteURL: r,
        isExternal: i,
        to: n
    }
}
Object.getOwnPropertyNames(Object.prototype).sort().join(`\0`);
var Ae = [`POST`, `PUT`, `PATCH`, `DELETE`];
new Set(Ae);
var je = [`GET`, ...Ae];
new Set(je);
var L = v.createContext(null);
L.displayName = `DataRouter`;
var R = v.createContext(null);
R.displayName = `DataRouterState`;
var Me = v.createContext(!1)
  , Ne = v.createContext({
    isTransitioning: !1
});
Ne.displayName = `ViewTransition`;
var Pe = v.createContext(new Map);
Pe.displayName = `Fetchers`;
var Fe = v.createContext(null);
Fe.displayName = `Await`;
var z = v.createContext(null);
z.displayName = `Navigation`;
var B = v.createContext(null);
B.displayName = `Location`;
var V = v.createContext({
    outlet: null,
    matches: [],
    isDataRoute: !1
});
V.displayName = `Route`;
var Ie = v.createContext(null);
Ie.displayName = `RouteError`;
var Le = `REACT_ROUTER_ERROR`
  , Re = `REDIRECT`
  , ze = `ROUTE_ERROR_RESPONSE`;
function Be(e) {
    if (e.startsWith(`${Le}:${Re}:{`))
        try {
            let t = JSON.parse(e.slice(28));
            if (typeof t == `object` && t && typeof t.status == `number` && typeof t.statusText == `string` && typeof t.location == `string` && typeof t.reloadDocument == `boolean` && typeof t.replace == `boolean`)
                return t
        } catch {}
}
function Ve(e) {
    if (e.startsWith(`${Le}:${ze}:{`))
        try {
            let t = JSON.parse(e.slice(40));
            if (typeof t == `object` && t && typeof t.status == `number` && typeof t.statusText == `string`)
                return new Te(t.status,t.statusText,t.data)
        } catch {}
}
function He(e, {relative: t}={}) {
    S(H(), `useHref() may be used only in the context of a <Router> component.`);
    let {basename: n, navigator: r} = v.useContext(z)
      , {hash: i, pathname: a, search: o} = W(e, {
        relative: t
    })
      , s = a;
    return n !== `/` && (s = a === `/` ? n : I([n, a])),
    r.createHref({
        pathname: s,
        search: o,
        hash: i
    })
}
function H() {
    return v.useContext(B) != null
}
function U() {
    return S(H(), `useLocation() may be used only in the context of a <Router> component.`),
    v.useContext(B).location
}
var Ue = `You should call navigate() in a React.useEffect(), not when your component is first rendered.`;
function We(e) {
    v.useContext(z).static || v.useLayoutEffect(e)
}
function Ge() {
    let {isDataRoute: e} = v.useContext(V);
    return e ? dt() : Ke()
}
function Ke() {
    S(H(), `useNavigate() may be used only in the context of a <Router> component.`);
    let e = v.useContext(L)
      , {basename: t, navigator: n} = v.useContext(z)
      , {matches: r} = v.useContext(V)
      , {pathname: i} = U()
      , a = JSON.stringify(be(r))
      , o = v.useRef(!1);
    return We( () => {
        o.current = !0
    }
    ),
    v.useCallback( (r, s={}) => {
        if (C(o.current, Ue),
        !o.current)
            return;
        if (typeof r == `number`) {
            n.go(r);
            return
        }
        let c = xe(r, JSON.parse(a), i, s.relative === `path`);
        e == null && t !== `/` && (c.pathname = c.pathname === `/` ? t : I([t, c.pathname])),
        (s.replace ? n.replace : n.push)(c, s.state, s)
    }
    , [t, n, a, i, e])
}
v.createContext(null);
function W(e, {relative: t}={}) {
    let {matches: n} = v.useContext(V)
      , {pathname: r} = U()
      , i = JSON.stringify(be(n));
    return v.useMemo( () => xe(e, JSON.parse(i), r, t === `path`), [e, i, r, t])
}
function qe(e, t) {
    return Je(e, t)
}
function Je(e, t, n) {
    S(H(), `useRoutes() may be used only in the context of a <Router> component.`);
    let {navigator: r} = v.useContext(z)
      , {matches: i} = v.useContext(V)
      , a = i[i.length - 1]
      , o = a ? a.params : {}
      , s = a ? a.pathname : `/`
      , c = a ? a.pathnameBase : `/`
      , l = a && a.route;
    {
        let e = l && l.path || ``;
        pt(s, !l || e.endsWith(`*`) || e.endsWith(`*?`), `You rendered descendant <Routes> (or called \`useRoutes()\`) at "${s}" (under <Route path="${e}">) but the parent route path has no trailing "*". This means if you navigate deeper, the parent won't match anymore and therefore the child routes will never render.

Please change the parent <Route path="${e}"> to <Route path="${e === `/` ? `*` : `${e}/*`}">.`)
    }
    let u = U(), d;
    if (t) {
        let e = typeof t == `string` ? O(t) : t;
        S(c === `/` || e.pathname?.startsWith(c), `When overriding the location using \`<Routes location>\` or \`useRoutes(routes, location)\`, the location pathname must begin with the portion of the URL pathname that was matched by all parent routes. The current pathname base is "${c}" but pathname "${e.pathname}" was given in the \`location\` prop.`),
        d = e
    } else
        d = u;
    let f = d.pathname || `/`
      , p = f;
    if (c !== `/`) {
        let e = c.replace(/^\//, ``).split(`/`);
        p = `/` + f.replace(/^\//, ``).split(`/`).slice(e.length).join(`/`)
    }
    let m = j(e, {
        pathname: p
    });
    C(l || m != null, `No routes matched location "${d.pathname}${d.search}${d.hash}" `),
    C(m == null || m[m.length - 1].route.element !== void 0 || m[m.length - 1].route.Component !== void 0 || m[m.length - 1].route.lazy !== void 0, `Matched leaf route at location "${d.pathname}${d.search}${d.hash}" does not have an element or Component. This means it will render an <Outlet /> with a null value by default resulting in an "empty" page.`);
    let h = tt(m && m.map(e => Object.assign({}, e, {
        params: Object.assign({}, o, e.params),
        pathname: I([c, r.encodeLocation ? r.encodeLocation(e.pathname.replace(/%/g, `%25`).replace(/\?/g, `%3F`).replace(/#/g, `%23`)).pathname : e.pathname]),
        pathnameBase: e.pathnameBase === `/` ? c : I([c, r.encodeLocation ? r.encodeLocation(e.pathnameBase.replace(/%/g, `%25`).replace(/\?/g, `%3F`).replace(/#/g, `%23`)).pathname : e.pathnameBase])
    })), i, n);
    return t && h ? v.createElement(B.Provider, {
        value: {
            location: {
                pathname: `/`,
                search: ``,
                hash: ``,
                state: null,
                key: `default`,
                unstable_mask: void 0,
                ...d
            },
            navigationType: `POP`
        }
    }, h) : h
}
function Ye() {
    let e = ut()
      , t = Ee(e) ? `${e.status} ${e.statusText}` : e instanceof Error ? e.message : JSON.stringify(e)
      , n = e instanceof Error ? e.stack : null
      , r = `rgba(200,200,200, 0.5)`
      , i = {
        padding: `0.5rem`,
        backgroundColor: r
    }
      , a = {
        padding: `2px 4px`,
        backgroundColor: r
    }
      , o = null;
    return console.error(`Error handled by React Router default ErrorBoundary:`, e),
    o = v.createElement(v.Fragment, null, v.createElement(`p`, null, `💿 Hey developer 👋`), v.createElement(`p`, null, `You can provide a way better UX than this when your app throws errors by providing your own `, v.createElement(`code`, {
        style: a
    }, `ErrorBoundary`), ` or`, ` `, v.createElement(`code`, {
        style: a
    }, `errorElement`), ` prop on your route.`)),
    v.createElement(v.Fragment, null, v.createElement(`h2`, null, `Unexpected Application Error!`), v.createElement(`h3`, {
        style: {
            fontStyle: `italic`
        }
    }, t), n ? v.createElement(`pre`, {
        style: i
    }, n) : null, o)
}
var Xe = v.createElement(Ye, null)
  , Ze = class extends v.Component {
    constructor(e) {
        super(e),
        this.state = {
            location: e.location,
            revalidation: e.revalidation,
            error: e.error
        }
    }
    static getDerivedStateFromError(e) {
        return {
            error: e
        }
    }
    static getDerivedStateFromProps(e, t) {
        return t.location !== e.location || t.revalidation !== `idle` && e.revalidation === `idle` ? {
            error: e.error,
            location: e.location,
            revalidation: e.revalidation
        } : {
            error: e.error === void 0 ? t.error : e.error,
            location: t.location,
            revalidation: e.revalidation || t.revalidation
        }
    }
    componentDidCatch(e, t) {
        this.props.onError ? this.props.onError(e, t) : console.error(`React Router caught the following error during render`, e)
    }
    render() {
        let e = this.state.error;
        if (this.context && typeof e == `object` && e && `digest`in e && typeof e.digest == `string`) {
            let t = Ve(e.digest);
            t && (e = t)
        }
        let t = e === void 0 ? this.props.children : v.createElement(V.Provider, {
            value: this.props.routeContext
        }, v.createElement(Ie.Provider, {
            value: e,
            children: this.props.component
        }));
        return this.context ? v.createElement($e, {
            error: e
        }, t) : t
    }
}
;
Ze.contextType = Me;
var Qe = new WeakMap;
function $e({children: e, error: t}) {
    let {basename: n} = v.useContext(z);
    if (typeof t == `object` && t && `digest`in t && typeof t.digest == `string`) {
        let e = Be(t.digest);
        if (e) {
            let r = Qe.get(t);
            if (r)
                throw r;
            let i = ke(e.location, n);
            if (Oe && !Qe.get(t))
                if (i.isExternal || e.reloadDocument)
                    window.location.href = i.absoluteURL || i.to;
                else {
                    let n = Promise.resolve().then( () => window.__reactRouterDataRouter.navigate(i.to, {
                        replace: e.replace
                    }));
                    throw Qe.set(t, n),
                    n
                }
            return v.createElement(`meta`, {
                httpEquiv: `refresh`,
                content: `0;url=${i.absoluteURL || i.to}`
            })
        }
    }
    return e
}
function et({routeContext: e, match: t, children: n}) {
    let r = v.useContext(L);
    return r && r.static && r.staticContext && (t.route.errorElement || t.route.ErrorBoundary) && (r.staticContext._deepestRenderedBoundaryId = t.route.id),
    v.createElement(V.Provider, {
        value: e
    }, n)
}
function tt(e, t=[], n) {
    let r = n?.state;
    if (e == null) {
        if (!r)
            return null;
        if (r.errors)
            e = r.matches;
        else if (t.length === 0 && !r.initialized && r.matches.length > 0)
            e = r.matches;
        else
            return null
    }
    let i = e
      , a = r?.errors;
    if (a != null) {
        let e = i.findIndex(e => e.route.id && a?.[e.route.id] !== void 0);
        S(e >= 0, `Could not find a matching route for errors on route IDs: ${Object.keys(a).join(`,`)}`),
        i = i.slice(0, Math.min(i.length, e + 1))
    }
    let o = !1
      , s = -1;
    if (n && r) {
        o = r.renderFallback;
        for (let e = 0; e < i.length; e++) {
            let t = i[e];
            if ((t.route.HydrateFallback || t.route.hydrateFallbackElement) && (s = e),
            t.route.id) {
                let {loaderData: e, errors: a} = r
                  , c = t.route.loader && !e.hasOwnProperty(t.route.id) && (!a || a[t.route.id] === void 0);
                if (t.route.lazy || c) {
                    n.isStatic && (o = !0),
                    i = s >= 0 ? i.slice(0, s + 1) : [i[0]];
                    break
                }
            }
        }
    }
    let c = n?.onError
      , l = r && c ? (e, t) => {
        c(e, {
            location: r.location,
            params: r.matches?.[0]?.params ?? {},
            unstable_pattern: De(r.matches),
            errorInfo: t
        })
    }
    : void 0;
    return i.reduceRight( (e, n, c) => {
        let u, d = !1, f = null, p = null;
        r && (u = a && n.route.id ? a[n.route.id] : void 0,
        f = n.route.errorElement || Xe,
        o && (s < 0 && c === 0 ? (pt(`route-fallback`, !1, "No `HydrateFallback` element provided to render during initial hydration"),
        d = !0,
        p = null) : s === c && (d = !0,
        p = n.route.hydrateFallbackElement || null)));
        let m = t.concat(i.slice(0, c + 1))
          , h = () => {
            let t;
            return t = u ? f : d ? p : n.route.Component ? v.createElement(n.route.Component, null) : n.route.element ? n.route.element : e,
            v.createElement(et, {
                match: n,
                routeContext: {
                    outlet: e,
                    matches: m,
                    isDataRoute: r != null
                },
                children: t
            })
        }
        ;
        return r && (n.route.ErrorBoundary || n.route.errorElement || c === 0) ? v.createElement(Ze, {
            location: r.location,
            revalidation: r.revalidation,
            component: f,
            error: u,
            children: h(),
            routeContext: {
                outlet: null,
                matches: m,
                isDataRoute: !0
            },
            onError: l
        }) : h()
    }
    , null)
}
function nt(e) {
    return `${e} must be used within a data router.  See https://reactrouter.com/en/main/routers/picking-a-router.`
}
function rt(e) {
    let t = v.useContext(L);
    return S(t, nt(e)),
    t
}
function it(e) {
    let t = v.useContext(R);
    return S(t, nt(e)),
    t
}
function at(e) {
    let t = v.useContext(V);
    return S(t, nt(e)),
    t
}
function ot(e) {
    let t = at(e)
      , n = t.matches[t.matches.length - 1];
    return S(n.route.id, `${e} can only be used on routes that contain a unique "id"`),
    n.route.id
}
function st() {
    return ot(`useRouteId`)
}
function ct() {
    return it(`useNavigation`).navigation
}
function lt() {
    let {matches: e, loaderData: t} = it(`useMatches`);
    return v.useMemo( () => e.map(e => M(e, t)), [e, t])
}
function ut() {
    let e = v.useContext(Ie)
      , t = it(`useRouteError`)
      , n = ot(`useRouteError`);
    return e === void 0 ? t.errors?.[n] : e
}
function dt() {
    let {router: e} = rt(`useNavigate`)
      , t = ot(`useNavigate`)
      , n = v.useRef(!1);
    return We( () => {
        n.current = !0
    }
    ),
    v.useCallback(async (r, i={}) => {
        C(n.current, Ue),
        n.current && (typeof r == `number` ? await e.navigate(r) : await e.navigate(r, {
            fromRouteId: t,
            ...i
        }))
    }
    , [e, t])
}
var ft = {};
function pt(e, t, n) {
    !t && !ft[e] && (ft[e] = !0,
    C(!1, n))
}
v.useOptimistic,
v.memo(mt);
function mt({routes: e, future: t, state: n, isStatic: r, onError: i}) {
    return Je(e, void 0, {
        state: n,
        isStatic: r,
        onError: i,
        future: t
    })
}
function ht({basename: e=`/`, children: t=null, location: n, navigationType: r=`POP`, navigator: i, static: a=!1, unstable_useTransitions: o}) {
    S(!H(), `You cannot render a <Router> inside another <Router>. You should never have more than one in your app.`);
    let s = e.replace(/^\/*/, `/`)
      , c = v.useMemo( () => ({
        basename: s,
        navigator: i,
        static: a,
        unstable_useTransitions: o,
        future: {}
    }), [s, i, a, o]);
    typeof n == `string` && (n = O(n));
    let {pathname: l=`/`, search: u=``, hash: d=``, state: f=null, key: p=`default`, unstable_mask: m} = n
      , h = v.useMemo( () => {
        let e = F(l, s);
        return e == null ? null : {
            location: {
                pathname: e,
                search: u,
                hash: d,
                state: f,
                key: p,
                unstable_mask: m
            },
            navigationType: r
        }
    }
    , [s, l, u, d, f, p, r, m]);
    return C(h != null, `<Router basename="${s}"> is not able to match the URL "${l}${u}${d}" because it does not start with the basename, so the <Router> won't render anything.`),
    h == null ? null : v.createElement(z.Provider, {
        value: c
    }, v.createElement(B.Provider, {
        children: t,
        value: h
    }))
}
var G = `get`
  , K = `application/x-www-form-urlencoded`;
function q(e) {
    return typeof HTMLElement < `u` && e instanceof HTMLElement
}
function gt(e) {
    return q(e) && e.tagName.toLowerCase() === `button`
}
function _t(e) {
    return q(e) && e.tagName.toLowerCase() === `form`
}
function vt(e) {
    return q(e) && e.tagName.toLowerCase() === `input`
}
function yt(e) {
    return !!(e.metaKey || e.altKey || e.ctrlKey || e.shiftKey)
}
function bt(e, t) {
    return e.button === 0 && (!t || t === `_self`) && !yt(e)
}
var J = null;
function xt() {
    if (J === null)
        try {
            new FormData(document.createElement(`form`),0),
            J = !1
        } catch {
            J = !0
        }
    return J
}
var St = new Set([`application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`]);
function Ct(e) {
    return e != null && !St.has(e) ? (C(!1, `"${e}" is not a valid \`encType\` for \`<Form>\`/\`<fetcher.Form>\` and will default to "${K}"`),
    null) : e
}
function wt(e, t) {
    let n, r, i, a, o;
    if (_t(e)) {
        let o = e.getAttribute(`action`);
        r = o ? F(o, t) : null,
        n = e.getAttribute(`method`) || G,
        i = Ct(e.getAttribute(`enctype`)) || K,
        a = new FormData(e)
    } else if (gt(e) || vt(e) && (e.type === `submit` || e.type === `image`)) {
        let o = e.form;
        if (o == null)
            throw Error(`Cannot submit a <button> or <input type="submit"> without a <form>`);
        let s = e.getAttribute(`formaction`) || o.getAttribute(`action`);
        if (r = s ? F(s, t) : null,
        n = e.getAttribute(`formmethod`) || o.getAttribute(`method`) || G,
        i = Ct(e.getAttribute(`formenctype`)) || Ct(o.getAttribute(`enctype`)) || K,
        a = new FormData(o,e),
        !xt()) {
            let {name: t, type: n, value: r} = e;
            if (n === `image`) {
                let e = t ? `${t}.` : ``;
                a.append(`${e}x`, `0`),
                a.append(`${e}y`, `0`)
            } else
                t && a.append(t, r)
        }
    } else if (q(e))
        throw Error(`Cannot submit element that is not <form>, <button>, or <input type="submit|image">`);
    else
        n = G,
        r = null,
        i = K,
        o = e;
    return a && i === `text/plain` && (o = a,
    a = void 0),
    {
        action: r,
        method: n.toLowerCase(),
        encType: i,
        formData: a,
        body: o
    }
}
Object.getOwnPropertyNames(Object.prototype).sort().join(`\0`);
var Tt = {
    "&": `\\u0026`,
    ">": `\\u003e`,
    "<": `\\u003c`,
    "\u2028": `\\u2028`,
    "\u2029": `\\u2029`
}
  , Et = /[&><\u2028\u2029]/g;
function Dt(e) {
    return e.replace(Et, e => Tt[e])
}
function Ot(e, t) {
    if (e === !1 || e == null)
        throw Error(t)
}
function kt(e, t, n, r) {
    let i = typeof e == `string` ? new URL(e,typeof window > `u` ? `server://singlefetch/` : window.location.origin) : e;
    return n ? i.pathname.endsWith(`/`) ? i.pathname = `${i.pathname}_.${r}` : i.pathname = `${i.pathname}.${r}` : i.pathname === `/` ? i.pathname = `_root.${r}` : t && F(i.pathname, t) === `/` ? i.pathname = `${t.replace(/\/$/, ``)}/_root.${r}` : i.pathname = `${i.pathname.replace(/\/$/, ``)}.${r}`,
    i
}
async function At(e, t) {
    if (e.id in t)
        return t[e.id];
    try {
        let n = await p( () => import(e.module), []);
        return t[e.id] = n,
        n
    } catch (t) {
        return console.error(`Error loading route module \`${e.module}\`, reloading page...`),
        console.error(t),
        window.__reactRouterContext && window.__reactRouterContext.isSpaMode,
        window.location.reload(),
        new Promise( () => {}
        )
    }
}
function jt(e) {
    return e != null && typeof e.page == `string`
}
function Mt(e) {
    return e == null ? !1 : e.href == null ? e.rel === `preload` && typeof e.imageSrcSet == `string` && typeof e.imageSizes == `string` : typeof e.rel == `string` && typeof e.href == `string`
}
async function Nt(e, t, n) {
    return Rt((await Promise.all(e.map(async e => {
        let r = t.routes[e.route.id];
        if (r) {
            let e = await At(r, n);
            return e.links ? e.links() : []
        }
        return []
    }
    ))).flat(1).filter(Mt).filter(e => e.rel === `stylesheet` || e.rel === `preload`).map(e => e.rel === `stylesheet` ? {
        ...e,
        rel: `prefetch`,
        as: `style`
    } : {
        ...e,
        rel: `prefetch`
    }))
}
function Pt(e, t, n, r, i, a) {
    let o = (e, t) => n[t] ? e.route.id !== n[t].route.id : !0
      , s = (e, t) => n[t].pathname !== e.pathname || n[t].route.path?.endsWith(`*`) && n[t].params[`*`] !== e.params[`*`];
    return a === `assets` ? t.filter( (e, t) => o(e, t) || s(e, t)) : a === `data` ? t.filter( (t, a) => {
        let c = r.routes[t.route.id];
        if (!c || !c.hasLoader)
            return !1;
        if (o(t, a) || s(t, a))
            return !0;
        if (t.route.shouldRevalidate) {
            let r = t.route.shouldRevalidate({
                currentUrl: new URL(i.pathname + i.search + i.hash,window.origin),
                currentParams: n[0]?.params || {},
                nextUrl: new URL(e,window.origin),
                nextParams: t.params,
                defaultShouldRevalidate: !0
            });
            if (typeof r == `boolean`)
                return r
        }
        return !0
    }
    ) : []
}
function Ft(e, t, {includeHydrateFallback: n}={}) {
    return It(e.map(e => {
        let r = t.routes[e.route.id];
        if (!r)
            return [];
        let i = [r.module];
        return r.clientActionModule && (i = i.concat(r.clientActionModule)),
        r.clientLoaderModule && (i = i.concat(r.clientLoaderModule)),
        n && r.hydrateFallbackModule && (i = i.concat(r.hydrateFallbackModule)),
        r.imports && (i = i.concat(r.imports)),
        i
    }
    ).flat(1))
}
function It(e) {
    return [...new Set(e)]
}
function Lt(e) {
    let t = {}
      , n = Object.keys(e).sort();
    for (let r of n)
        t[r] = e[r];
    return t
}
function Rt(e, t) {
    let n = new Set
      , r = new Set(t);
    return e.reduce( (e, i) => {
        if (t && !jt(i) && i.as === `script` && i.href && r.has(i.href))
            return e;
        let a = JSON.stringify(Lt(i));
        return n.has(a) || (n.add(a),
        e.push({
            key: a,
            link: i
        })),
        e
    }
    , [])
}
function zt() {
    let e = v.useContext(L);
    return Ot(e, `You must render this element inside a <DataRouterContext.Provider> element`),
    e
}
function Bt() {
    let e = v.useContext(R);
    return Ot(e, `You must render this element inside a <DataRouterStateContext.Provider> element`),
    e
}
var Y = v.createContext(void 0);
Y.displayName = `FrameworkContext`;
function Vt() {
    let e = v.useContext(Y);
    return Ot(e, `You must render this element inside a <HydratedRouter> element`),
    e
}
function Ht(e, t) {
    let n = v.useContext(Y)
      , [r,i] = v.useState(!1)
      , [a,o] = v.useState(!1)
      , {onFocus: s, onBlur: c, onMouseEnter: l, onMouseLeave: u, onTouchStart: d} = t
      , f = v.useRef(null);
    v.useEffect( () => {
        if (e === `render` && o(!0),
        e === `viewport`) {
            let e = new IntersectionObserver(e => {
                e.forEach(e => {
                    o(e.isIntersecting)
                }
                )
            }
            ,{
                threshold: .5
            });
            return f.current && e.observe(f.current),
            () => {
                e.disconnect()
            }
        }
    }
    , [e]),
    v.useEffect( () => {
        if (r) {
            let e = setTimeout( () => {
                o(!0)
            }
            , 100);
            return () => {
                clearTimeout(e)
            }
        }
    }
    , [r]);
    let p = () => {
        i(!0)
    }
      , m = () => {
        i(!1),
        o(!1)
    }
    ;
    return n ? e === `intent` ? [a, f, {
        onFocus: X(s, p),
        onBlur: X(c, m),
        onMouseEnter: X(l, p),
        onMouseLeave: X(u, m),
        onTouchStart: X(d, p)
    }] : [a, f, {}] : [!1, f, {}]
}
function X(e, t) {
    return n => {
        e && e(n),
        n.defaultPrevented || t(n)
    }
}
function Ut({page: e, ...t}) {
    let {router: n} = zt()
      , r = v.useMemo( () => j(n.routes, e, n.basename), [n.routes, e, n.basename]);
    return r ? v.createElement(Gt, {
        page: e,
        matches: r,
        ...t
    }) : null
}
function Wt(e) {
    let {manifest: t, routeModules: n} = Vt()
      , [r,i] = v.useState([]);
    return v.useEffect( () => {
        let r = !1;
        return Nt(e, t, n).then(e => {
            r || i(e)
        }
        ),
        () => {
            r = !0
        }
    }
    , [e, t, n]),
    r
}
function Gt({page: e, matches: t, ...n}) {
    let r = U()
      , {future: i, manifest: a, routeModules: o} = Vt()
      , {basename: s} = zt()
      , {loaderData: c, matches: l} = Bt()
      , u = v.useMemo( () => Pt(e, t, l, a, r, `data`), [e, t, l, a, r])
      , d = v.useMemo( () => Pt(e, t, l, a, r, `assets`), [e, t, l, a, r])
      , f = v.useMemo( () => {
        if (e === r.pathname + r.search + r.hash)
            return [];
        let n = new Set
          , l = !1;
        if (t.forEach(e => {
            let t = a.routes[e.route.id];
            !t || !t.hasLoader || (!u.some(t => t.route.id === e.route.id) && e.route.id in c && o[e.route.id]?.shouldRevalidate || t.hasClientLoader ? l = !0 : n.add(e.route.id))
        }
        ),
        n.size === 0)
            return [];
        let d = kt(e, s, i.unstable_trailingSlashAwareDataRequests, `data`);
        return l && n.size > 0 && d.searchParams.set(`_routes`, t.filter(e => n.has(e.route.id)).map(e => e.route.id).join(`,`)),
        [d.pathname + d.search]
    }
    , [s, i.unstable_trailingSlashAwareDataRequests, c, r, a, u, t, e, o])
      , p = v.useMemo( () => Ft(d, a), [d, a])
      , m = Wt(d);
    return v.createElement(v.Fragment, null, f.map(e => v.createElement(`link`, {
        key: e,
        rel: `prefetch`,
        as: `fetch`,
        href: e,
        ...n
    })), p.map(e => v.createElement(`link`, {
        key: e,
        rel: `modulepreload`,
        href: e,
        ...n
    })), m.map( ({key: e, link: t}) => v.createElement(`link`, {
        key: e,
        nonce: n.nonce,
        ...t,
        crossOrigin: t.crossOrigin ?? n.crossOrigin
    })))
}
function Kt(...e) {
    return t => {
        e.forEach(e => {
            typeof e == `function` ? e(t) : e != null && (e.current = t)
        }
        )
    }
}
var qt = typeof window < `u` && window.document !== void 0 && window.document.createElement !== void 0;
try {
    qt && (window.__reactRouterVersion = `7.13.2`)
} catch {}
function Jt({basename: e, children: t, unstable_useTransitions: n, window: r}) {
    let i = v.useRef();
    i.current ??= x({
        window: r,
        v5Compat: !0
    });
    let a = i.current
      , [o,s] = v.useState({
        action: a.action,
        location: a.location
    })
      , c = v.useCallback(e => {
        n === !1 ? s(e) : v.startTransition( () => s(e))
    }
    , [n]);
    return v.useLayoutEffect( () => a.listen(c), [a, c]),
    v.createElement(ht, {
        basename: e,
        children: t,
        location: o.location,
        navigationType: o.action,
        navigator: a,
        unstable_useTransitions: n
    })
}
function Yt({basename: e, children: t, history: n, unstable_useTransitions: r}) {
    let[i,a] = v.useState({
        action: n.action,
        location: n.location
    })
      , o = v.useCallback(e => {
        r === !1 ? a(e) : v.startTransition( () => a(e))
    }
    , [r]);
    return v.useLayoutEffect( () => n.listen(o), [n, o]),
    v.createElement(ht, {
        basename: e,
        children: t,
        location: i.location,
        navigationType: i.action,
        navigator: n,
        unstable_useTransitions: r
    })
}
Yt.displayName = `unstable_HistoryRouter`;
var Xt = /^(?:[a-z][a-z0-9+.-]*:|\/\/)/i
  , Zt = v.forwardRef(function({onClick: e, discover: t=`render`, prefetch: n=`none`, relative: r, reloadDocument: i, replace: a, unstable_mask: o, state: s, target: c, to: l, preventScrollReset: u, viewTransition: d, unstable_defaultShouldRevalidate: f, ...p}, m) {
    let {basename: h, navigator: g, unstable_useTransitions: _} = v.useContext(z)
      , y = typeof l == `string` && Xt.test(l)
      , b = ke(l, h);
    l = b.to;
    let x = He(l, {
        relative: r
    })
      , S = U()
      , C = null;
    if (o) {
        let e = xe(o, [], S.unstable_mask ? S.unstable_mask.pathname : `/`, !0);
        h !== `/` && (e.pathname = e.pathname === `/` ? h : I([h, e.pathname])),
        C = g.createHref(e)
    }
    let[w,T,E] = Ht(n, p)
      , D = rn(l, {
        replace: a,
        unstable_mask: o,
        state: s,
        target: c,
        preventScrollReset: u,
        relative: r,
        viewTransition: d,
        unstable_defaultShouldRevalidate: f,
        unstable_useTransitions: _
    });
    function O(t) {
        e && e(t),
        t.defaultPrevented || D(t)
    }
    let k = !(b.isExternal || i)
      , A = v.createElement(`a`, {
        ...p,
        ...E,
        href: (k ? C : void 0) || b.absoluteURL || x,
        onClick: k ? O : e,
        ref: Kt(m, T),
        target: c,
        "data-discover": !y && t === `render` ? `true` : void 0
    });
    return w && !y ? v.createElement(v.Fragment, null, A, v.createElement(Ut, {
        page: x
    })) : A
});
Zt.displayName = `Link`;
var Qt = v.forwardRef(function({"aria-current": e=`page`, caseSensitive: t=!1, className: n=``, end: r=!1, style: i, to: a, viewTransition: o, children: s, ...c}, l) {
    let u = W(a, {
        relative: c.relative
    })
      , d = U()
      , f = v.useContext(R)
      , {navigator: p, basename: m} = v.useContext(z)
      , h = f != null && pn(u) && o === !0
      , g = p.encodeLocation ? p.encodeLocation(u).pathname : u.pathname
      , _ = d.pathname
      , y = f && f.navigation && f.navigation.location ? f.navigation.location.pathname : null;
    t || (_ = _.toLowerCase(),
    y = y ? y.toLowerCase() : null,
    g = g.toLowerCase()),
    y && m && (y = F(y, m) || y);
    let b = g !== `/` && g.endsWith(`/`) ? g.length - 1 : g.length, x = _ === g || !r && _.startsWith(g) && _.charAt(b) === `/`, S = y != null && (y === g || !r && y.startsWith(g) && y.charAt(g.length) === `/`), C = {
        isActive: x,
        isPending: S,
        isTransitioning: h
    }, w = x ? e : void 0, T;
    T = typeof n == `function` ? n(C) : [n, x ? `active` : null, S ? `pending` : null, h ? `transitioning` : null].filter(Boolean).join(` `);
    let E = typeof i == `function` ? i(C) : i;
    return v.createElement(Zt, {
        ...c,
        "aria-current": w,
        className: T,
        ref: l,
        style: E,
        to: a,
        viewTransition: o
    }, typeof s == `function` ? s(C) : s)
});
Qt.displayName = `NavLink`;
var $t = v.forwardRef( ({discover: e=`render`, fetcherKey: t, navigate: n, reloadDocument: r, replace: i, state: a, method: o=G, action: s, onSubmit: c, relative: l, preventScrollReset: u, viewTransition: d, unstable_defaultShouldRevalidate: f, ...p}, m) => {
    let {unstable_useTransitions: h} = v.useContext(z)
      , g = sn()
      , _ = cn(s, {
        relative: l
    })
      , y = o.toLowerCase() === `get` ? `get` : `post`
      , b = typeof s == `string` && Xt.test(s);
    return v.createElement(`form`, {
        ref: m,
        method: y,
        action: _,
        onSubmit: r ? c : e => {
            if (c && c(e),
            e.defaultPrevented)
                return;
            e.preventDefault();
            let r = e.nativeEvent.submitter
              , s = r?.getAttribute(`formmethod`) || o
              , p = () => g(r || e.currentTarget, {
                fetcherKey: t,
                method: s,
                navigate: n,
                replace: i,
                state: a,
                relative: l,
                preventScrollReset: u,
                viewTransition: d,
                unstable_defaultShouldRevalidate: f
            });
            h && n !== !1 ? v.startTransition( () => p()) : p()
        }
        ,
        ...p,
        "data-discover": !b && e === `render` ? `true` : void 0
    })
}
);
$t.displayName = `Form`;
function en({getKey: e, storageKey: t, ...n}) {
    let r = v.useContext(Y)
      , {basename: i} = v.useContext(z)
      , a = U()
      , o = lt();
    dn({
        getKey: e,
        storageKey: t
    });
    let s = v.useMemo( () => {
        if (!r || !e)
            return null;
        let t = un(a, o, i, e);
        return t === a.key ? null : t
    }
    , []);
    if (!r || r.isSpaMode)
        return null;
    let c = ( (e, t) => {
        if (!window.history.state || !window.history.state.key) {
            let e = Math.random().toString(32).slice(2);
            window.history.replaceState({
                key: e
            }, ``)
        }
        try {
            let n = JSON.parse(sessionStorage.getItem(e) || `{}`)[t || window.history.state.key];
            typeof n == `number` && window.scrollTo(0, n)
        } catch (t) {
            console.error(t),
            sessionStorage.removeItem(e)
        }
    }
    ).toString();
    return v.createElement(`script`, {
        ...n,
        suppressHydrationWarning: !0,
        dangerouslySetInnerHTML: {
            __html: `(${c})(${Dt(JSON.stringify(t || ln))}, ${Dt(JSON.stringify(s))})`
        }
    })
}
en.displayName = `ScrollRestoration`;
function tn(e) {
    return `${e} must be used within a data router.  See https://reactrouter.com/en/main/routers/picking-a-router.`
}
function Z(e) {
    let t = v.useContext(L);
    return S(t, tn(e)),
    t
}
function nn(e) {
    let t = v.useContext(R);
    return S(t, tn(e)),
    t
}
function rn(e, {target: t, replace: n, unstable_mask: r, state: i, preventScrollReset: a, relative: o, viewTransition: s, unstable_defaultShouldRevalidate: c, unstable_useTransitions: l}={}) {
    let u = Ge()
      , d = U()
      , f = W(e, {
        relative: o
    });
    return v.useCallback(p => {
        if (bt(p, t)) {
            p.preventDefault();
            let t = n === void 0 ? D(d) === D(f) : n
              , m = () => u(e, {
                replace: t,
                unstable_mask: r,
                state: i,
                preventScrollReset: a,
                relative: o,
                viewTransition: s,
                unstable_defaultShouldRevalidate: c
            });
            l ? v.startTransition( () => m()) : m()
        }
    }
    , [d, u, f, n, r, i, t, e, a, o, s, c, l])
}
var an = 0
  , on = () => `__${String(++an)}__`;
function sn() {
    let {router: e} = Z(`useSubmit`)
      , {basename: t} = v.useContext(z)
      , n = st()
      , r = e.fetch
      , i = e.navigate;
    return v.useCallback(async (e, a={}) => {
        let {action: o, method: s, encType: c, formData: l, body: u} = wt(e, t);
        a.navigate === !1 ? await r(a.fetcherKey || on(), n, a.action || o, {
            unstable_defaultShouldRevalidate: a.unstable_defaultShouldRevalidate,
            preventScrollReset: a.preventScrollReset,
            formData: l,
            body: u,
            formMethod: a.method || s,
            formEncType: a.encType || c,
            flushSync: a.flushSync
        }) : await i(a.action || o, {
            unstable_defaultShouldRevalidate: a.unstable_defaultShouldRevalidate,
            preventScrollReset: a.preventScrollReset,
            formData: l,
            body: u,
            formMethod: a.method || s,
            formEncType: a.encType || c,
            replace: a.replace,
            state: a.state,
            fromRouteId: n,
            flushSync: a.flushSync,
            viewTransition: a.viewTransition
        })
    }
    , [r, i, t, n])
}
function cn(e, {relative: t}={}) {
    let {basename: n} = v.useContext(z)
      , r = v.useContext(V);
    S(r, `useFormAction must be used inside a RouteContext`);
    let[i] = r.matches.slice(-1)
      , a = {
        ...W(e || `.`, {
            relative: t
        })
    }
      , o = U();
    if (e == null) {
        a.search = o.search;
        let e = new URLSearchParams(a.search)
          , t = e.getAll(`index`);
        if (t.some(e => e === ``)) {
            e.delete(`index`),
            t.filter(e => e).forEach(t => e.append(`index`, t));
            let n = e.toString();
            a.search = n ? `?${n}` : ``
        }
    }
    return (!e || e === `.`) && i.route.index && (a.search = a.search ? a.search.replace(/^\?/, `?index&`) : `?index`),
    n !== `/` && (a.pathname = a.pathname === `/` ? n : I([n, a.pathname])),
    D(a)
}
var ln = `react-router-scroll-positions`
  , Q = {};
function un(e, t, n, r) {
    let i = null;
    return r && (i = r(n === `/` ? e : {
        ...e,
        pathname: F(e.pathname, n) || e.pathname
    }, t)),
    i ??= e.key,
    i
}
function dn({getKey: e, storageKey: t}={}) {
    let {router: n} = Z(`useScrollRestoration`)
      , {restoreScrollPosition: r, preventScrollReset: i} = nn(`useScrollRestoration`)
      , {basename: a} = v.useContext(z)
      , o = U()
      , s = lt()
      , c = ct();
    v.useEffect( () => (window.history.scrollRestoration = `manual`,
    () => {
        window.history.scrollRestoration = `auto`
    }
    ), []),
    fn(v.useCallback( () => {
        if (c.state === `idle`) {
            let t = un(o, s, a, e);
            Q[t] = window.scrollY
        }
        try {
            sessionStorage.setItem(t || ln, JSON.stringify(Q))
        } catch (e) {
            C(!1, `Failed to save scroll positions in sessionStorage, <ScrollRestoration /> will not work properly (${e}).`)
        }
        window.history.scrollRestoration = `auto`
    }
    , [c.state, e, a, o, s, t])),
    typeof document < `u` && (v.useLayoutEffect( () => {
        try {
            let e = sessionStorage.getItem(t || ln);
            e && (Q = JSON.parse(e))
        } catch {}
    }
    , [t]),
    v.useLayoutEffect( () => {
        let t = n?.enableScrollRestoration(Q, () => window.scrollY, e ? (t, n) => un(t, n, a, e) : void 0);
        return () => t && t()
    }
    , [n, a, e]),
    v.useLayoutEffect( () => {
        if (r !== !1) {
            if (typeof r == `number`) {
                window.scrollTo(0, r);
                return
            }
            try {
                if (o.hash) {
                    let e = document.getElementById(decodeURIComponent(o.hash.slice(1)));
                    if (e) {
                        e.scrollIntoView();
                        return
                    }
                }
            } catch {
                C(!1, `"${o.hash.slice(1)}" is not a decodable element ID. The view will not scroll to it.`)
            }
            i !== !0 && window.scrollTo(0, 0)
        }
    }
    , [o, r, i]))
}
function fn(e, t) {
    let {capture: n} = t || {};
    v.useEffect( () => {
        let t = n == null ? void 0 : {
            capture: n
        };
        return window.addEventListener(`pagehide`, e, t),
        () => {
            window.removeEventListener(`pagehide`, e, t)
        }
    }
    , [e, n])
}
function pn(e, {relative: t}={}) {
    let n = v.useContext(Ne);
    S(n != null, "`useViewTransitionState` must be used within `react-router-dom`'s `RouterProvider`.  Did you accidentally import `RouterProvider` from `react-router`?");
    let {basename: r} = Z(`useViewTransitionState`)
      , i = W(e, {
        relative: t
    });
    if (!n.isTransitioning)
        return !1;
    let a = F(n.currentLocation.pathname, r) || n.currentLocation.pathname
      , o = F(n.nextLocation.pathname, r) || n.nextLocation.pathname;
    return P(i.pathname, o) != null || P(i.pathname, a) != null
}
var $ = l(_(), 1);
function mn() {
    let e = U();
    return (0,
    $.jsxs)(`div`, {
        className: `relative flex flex-col items-center justify-center h-screen text-center px-4`,
        children: [(0,
        $.jsx)(`h1`, {
            className: `absolute bottom-0 text-9xl md:text-[12rem] font-black text-gray-50 select-none pointer-events-none z-0`,
            children: `404`
        }), (0,
        $.jsxs)(`div`, {
            className: `relative z-10`,
            children: [(0,
            $.jsx)(`h1`, {
                className: `text-xl md:text-2xl font-semibold mt-6`,
                children: `This page has not been generated`
            }), (0,
            $.jsx)(`p`, {
                className: `mt-2 text-base text-gray-400 font-mono`,
                children: e.pathname
            }), (0,
            $.jsx)(`p`, {
                className: `mt-4 text-lg md:text-xl text-gray-500`,
                children: `Tell me more about this page, so I can generate it`
            })]
        })]
    })
}
var hn = () => {
    let[e,t] = (0,
    v.useState)(!1)
      , [n,r] = (0,
    v.useState)(!1);
    (0,
    v.useEffect)( () => {
        let e = () => t(window.scrollY > 40);
        return window.addEventListener(`scroll`, e),
        () => window.removeEventListener(`scroll`, e)
    }
    , []);
    let i = [`Features`, `How It Works`, `Marketplace`, `Pricing`];
    return (0,
    $.jsxs)(`header`, {
        className: `fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${e ? `bg-white/95 backdrop-blur-md border-b border-gray-200` : `bg-transparent`}`,
        children: [(0,
        $.jsxs)(`nav`, {
            className: `max-w-7xl mx-auto px-6 md:px-10 flex items-center justify-between h-16 md:h-20`,
            children: [(0,
            $.jsx)(`div`, {
                className: `flex items-center cursor-pointer`,
                children: (0,
                $.jsx)(`img`, {
                    src: `https://storage.readdy-site.link/project_files/6970c675-1c7b-4278-b8c2-58ef29f9255b/4b9d7d1d-270f-46de-a3a9-a737a8c62922_logo-transparency-01.png?v=d84c9cbf8bfd391ae42e9b405e652c8e`,
                    alt: `Logo`,
                    className: `h-10 md:h-12 w-auto object-contain`
                })
            }), (0,
            $.jsx)(`ul`, {
                className: `hidden md:flex items-center gap-8`,
                children: i.map(t => (0,
                $.jsx)(`li`, {
                    children: (0,
                    $.jsx)(`a`, {
                        href: `#`,
                        className: `text-sm transition-colors cursor-pointer whitespace-nowrap ${e ? `text-gray-600 hover:text-[#00C8E8]` : `text-gray-300 hover:text-[#00C8E8]`}`,
                        children: t
                    })
                }, t))
            }), (0,
            $.jsxs)(`div`, {
                className: `hidden md:flex items-center gap-3`,
                children: [(0,
                $.jsx)(`a`, {
                    href: `#`,
                    className: `text-sm transition-colors px-4 py-2 cursor-pointer whitespace-nowrap ${e ? `text-gray-700 hover:text-[#00C8E8]` : `text-gray-300 hover:text-white`}`,
                    children: `Log In`
                }), (0,
                $.jsx)(`a`, {
                    href: `#`,
                    className: `text-sm font-semibold text-[#050D1A] bg-[#00C8E8] px-5 py-2 rounded-full hover:bg-[#00E0FF] transition-colors cursor-pointer whitespace-nowrap`,
                    children: `Get Started`
                })]
            }), (0,
            $.jsx)(`button`, {
                className: `md:hidden w-8 h-8 flex items-center justify-center cursor-pointer ${e ? `text-gray-700` : `text-white`}`,
                onClick: () => r(!n),
                "aria-label": `Toggle menu`,
                children: (0,
                $.jsx)(`i`, {
                    className: `${n ? `ri-close-line` : `ri-menu-3-line`} text-xl`
                })
            })]
        }), n && (0,
        $.jsxs)(`div`, {
            className: `md:hidden border-b px-6 py-4 ${e ? `bg-white border-gray-200` : `bg-[#050D1A]/98 border-[#00C8E8]/10`}`,
            children: [(0,
            $.jsx)(`ul`, {
                className: `flex flex-col gap-4`,
                children: i.map(t => (0,
                $.jsx)(`li`, {
                    children: (0,
                    $.jsx)(`a`, {
                        href: `#`,
                        className: `transition-colors block py-1 cursor-pointer ${e ? `text-gray-600 hover:text-[#00C8E8]` : `text-gray-300 hover:text-[#00C8E8]`}`,
                        children: t
                    })
                }, t))
            }), (0,
            $.jsxs)(`div`, {
                className: `flex flex-col gap-3 mt-4 pt-4 border-t ${e ? `border-gray-200` : `border-white/10`}`,
                children: [(0,
                $.jsx)(`a`, {
                    href: `#`,
                    className: `text-center py-2 cursor-pointer ${e ? `text-gray-700` : `text-gray-300`}`,
                    children: `Log In`
                }), (0,
                $.jsx)(`a`, {
                    href: `#`,
                    className: `text-center text-sm font-semibold text-[#050D1A] bg-[#00C8E8] px-5 py-2.5 rounded-full cursor-pointer`,
                    children: `Get Started`
                })]
            })]
        })]
    })
}
  , gn = [`You don't always know who you're dealing with`, `Vouches don't carry from platform to platform`, `A post-it with a name and date can be easily faked`, `There's no protection if something goes wrong`]
  , _n = () => (0,
$.jsxs)(`section`, {
    className: `relative min-h-screen flex items-center overflow-hidden bg-[#050D1A]`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-20`,
        style: {
            backgroundImage: `linear-gradient(rgba(0,200,232,0.15) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0,200,232,0.15) 1px, transparent 1px)`,
            backgroundSize: `60px 60px`
        }
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 bg-[radial-gradient(ellipse_70%_60%_at_20%_50%,rgba(0,200,232,0.07),transparent)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 bg-[radial-gradient(ellipse_60%_80%_at_80%_50%,rgba(27,58,107,0.3),transparent)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute right-0 top-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-[radial-gradient(ellipse_at_center,rgba(0,200,232,0.10),transparent_70%)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute top-1/4 left-0 w-64 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/30 to-transparent`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute bottom-1/3 left-0 w-96 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/20 to-transparent`
    }), (0,
    $.jsx)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10 py-32 md:py-0 w-full`,
        children: (0,
        $.jsxs)(`div`, {
            className: `flex flex-col lg:flex-row items-center gap-12 lg:gap-16 min-h-screen`,
            children: [(0,
            $.jsxs)(`div`, {
                className: `flex-1 text-center lg:text-left lg:py-32`,
                children: [(0,
                $.jsxs)(`div`, {
                    className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/25 rounded-full px-4 py-1.5 mb-7`,
                    children: [(0,
                    $.jsx)(`span`, {
                        className: `w-1.5 h-1.5 rounded-full bg-[#00C8E8] inline-block`
                    }), (0,
                    $.jsx)(`span`, {
                        className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                        children: `Scam Protection Built In`
                    })]
                }), (0,
                $.jsxs)(`h1`, {
                    className: `text-4xl md:text-5xl lg:text-6xl font-extrabold leading-tight text-white mb-5`,
                    children: [`Don't Get Scammed`, ` `, (0,
                    $.jsx)(`span`, {
                        className: `text-transparent bg-clip-text block`,
                        style: {
                            backgroundImage: `linear-gradient(135deg, #00C8E8 0%, #00D4A8 100%)`
                        },
                        children: `& Stop Paying Fees.`
                    })]
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-300 text-base md:text-lg leading-relaxed max-w-xl mx-auto lg:mx-0 mb-4`,
                    children: `Card Trade protects your social deals from start to finish. Never send money blindly again.`
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-500 text-sm leading-relaxed max-w-xl mx-auto lg:mx-0 mb-6`,
                    children: `Card deals get risky when trust isn't clear.`
                }), (0,
                $.jsx)(`ul`, {
                    className: `flex flex-col gap-3 max-w-xl mx-auto lg:mx-0 mb-8`,
                    children: gn.map(e => (0,
                    $.jsxs)(`li`, {
                        className: `flex items-start gap-3 text-left`,
                        children: [(0,
                        $.jsx)(`span`, {
                            className: `mt-1 w-4 h-4 flex items-center justify-center flex-shrink-0`,
                            children: (0,
                            $.jsx)(`i`, {
                                className: `ri-close-circle-fill text-[#FF5C5C] text-base`
                            })
                        }), (0,
                        $.jsx)(`span`, {
                            className: `text-gray-400 text-sm leading-relaxed`,
                            children: e
                        })]
                    }, e))
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-500 text-xs italic max-w-xl mx-auto lg:mx-0 mb-8 border-l-2 border-[#00C8E8]/30 pl-3`,
                    children: `Collectors avoid marketplaces because of high fees, but social deals bring on risk.`
                }), (0,
                $.jsxs)(`div`, {
                    className: `flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4`,
                    children: [(0,
                    $.jsx)(`a`, {
                        href: `#`,
                        className: `w-full sm:w-auto bg-[#00C8E8] text-[#050D1A] font-bold text-sm px-8 py-3.5 rounded-full cursor-pointer whitespace-nowrap`,
                        style: {
                            boxShadow: `0 0 30px rgba(0,200,232,0.35)`
                        },
                        children: `Start Safe Trade`
                    }), (0,
                    $.jsxs)(`a`, {
                        href: `#`,
                        className: `w-full sm:w-auto flex items-center justify-center gap-2 border border-[#00C8E8]/30 text-white text-sm px-8 py-3.5 rounded-full cursor-pointer whitespace-nowrap hover:border-[#00C8E8]/60 transition-colors`,
                        children: [(0,
                        $.jsx)(`i`, {
                            className: `ri-user-add-line text-[#00C8E8]`
                        }), `Create Free Account`]
                    })]
                })]
            }), (0,
            $.jsxs)(`div`, {
                className: `flex-1 relative flex items-center justify-center min-h-[420px] lg:min-h-[600px] w-full`,
                children: [(0,
                $.jsx)(`div`, {
                    className: `absolute inset-0 flex items-center justify-center`,
                    children: (0,
                    $.jsx)(`div`, {
                        className: `w-80 h-80 md:w-[420px] md:h-[420px] rounded-full`,
                        style: {
                            background: `radial-gradient(circle, rgba(0,200,232,0.14) 0%, transparent 70%)`
                        }
                    })
                }), (0,
                $.jsx)(`div`, {
                    className: `absolute inset-8 border border-[#00C8E8]/08 rounded-3xl`,
                    style: {
                        clipPath: `polygon(4% 0%, 96% 0%, 100% 4%, 100% 96%, 96% 100%, 4% 100%, 0% 96%, 0% 4%)`
                    }
                }), (0,
                $.jsxs)(`div`, {
                    className: `relative z-10 w-full max-w-md mx-auto`,
                    children: [(0,
                    $.jsxs)(`div`, {
                        className: `absolute w-44 h-64 md:w-52 md:h-72 left-0 top-8 rounded-xl overflow-hidden border border-[#00C8E8]/20`,
                        style: {
                            transform: `rotate(-12deg) translateX(20px)`,
                            boxShadow: `0 20px 60px rgba(0,0,0,0.6)`
                        },
                        children: [(0,
                        $.jsx)(`img`, {
                            src: `https://readdy.ai/api/search-image?query=premium%20holographic%20Pok%C3%A9mon%20trading%20card%20Charizard%20holographic%20rare%20card%20on%20a%20sleek%20dark%20background%20with%20cyan%20glow%20effects%20dramatic%20studio%20lighting%20product%20photography%20ultra%20high%20quality%20cinematic&width=208&height=288&seq=hero-card-1&orientation=portrait`,
                            alt: `Trading card`,
                            className: `w-full h-full object-cover object-top`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute inset-0 bg-gradient-to-br from-[#00C8E8]/10 to-transparent`
                        })]
                    }), (0,
                    $.jsxs)(`div`, {
                        className: `absolute w-44 h-64 md:w-52 md:h-72 right-0 top-8 rounded-xl overflow-hidden border border-[#1B3A6B]/50`,
                        style: {
                            transform: `rotate(12deg) translateX(-20px)`,
                            boxShadow: `0 20px 60px rgba(0,0,0,0.6)`
                        },
                        children: [(0,
                        $.jsx)(`img`, {
                            src: `https://readdy.ai/api/search-image?query=premium%20sports%20trading%20card%20Michael%20Jordan%20basketball%20holographic%20foil%20rare%20collectible%20card%20on%20dark%20background%20with%20blue%20glow%20effects%20ultra%20high%20definition%20product%20photo&width=208&height=288&seq=hero-card-2&orientation=portrait`,
                            alt: `Trading card`,
                            className: `w-full h-full object-cover object-top`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute inset-0 bg-gradient-to-bl from-[#1B3A6B]/20 to-transparent`
                        })]
                    }), (0,
                    $.jsxs)(`div`, {
                        className: `relative mx-auto w-52 h-72 md:w-60 md:h-80 rounded-2xl overflow-hidden border-2 border-[#00C8E8]/40`,
                        style: {
                            boxShadow: `0 0 50px rgba(0,200,232,0.25), 0 30px 80px rgba(0,0,0,0.8)`
                        },
                        children: [(0,
                        $.jsx)(`img`, {
                            src: `https://readdy.ai/api/search-image?query=ultra%20rare%20premium%20holographic%20trading%20card%20Pikachu%20promo%20card%20with%20rainbow%20holographic%20foil%20effect%20dark%20background%20with%20intense%20cyan%20and%20teal%20glow%20premium%20collectible%20card%20photography%20cinematic&width=240&height=320&seq=hero-card-3&orientation=portrait`,
                            alt: `Featured trading card`,
                            className: `w-full h-full object-cover object-top`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute inset-0`,
                            style: {
                                background: `linear-gradient(135deg, rgba(0,200,232,0.15) 0%, transparent 40%, rgba(27,58,107,0.2) 100%)`
                            }
                        }), (0,
                        $.jsxs)(`div`, {
                            className: `absolute bottom-0 left-0 right-0 p-3 bg-gradient-to-t from-[#050D1A]/90 to-transparent`,
                            children: [(0,
                            $.jsx)(`div`, {
                                className: `text-xs font-bold text-white`,
                                children: `Pikachu #025`
                            }), (0,
                            $.jsxs)(`div`, {
                                className: `flex items-center gap-2 mt-0.5`,
                                children: [(0,
                                $.jsx)(`span`, {
                                    className: `text-[#00C8E8] text-xs font-semibold`,
                                    children: `$4,200`
                                }), (0,
                                $.jsx)(`span`, {
                                    className: `text-green-400 text-[10px] bg-green-400/10 px-1.5 py-0.5 rounded-full`,
                                    children: `+12.4%`
                                })]
                            })]
                        })]
                    }), (0,
                    $.jsxs)(`div`, {
                        className: `absolute -bottom-5 left-1/2 -translate-x-1/2 bg-[#0D1528]/90 backdrop-blur-sm border border-[#00C8E8]/25 rounded-xl px-4 py-2.5 flex items-center gap-2 whitespace-nowrap`,
                        style: {
                            boxShadow: `0 8px 32px rgba(0,0,0,0.4)`
                        },
                        children: [(0,
                        $.jsx)(`i`, {
                            className: `ri-shield-check-fill text-[#00C8E8] text-sm`
                        }), (0,
                        $.jsx)(`span`, {
                            className: `text-white text-xs font-medium`,
                            children: `Protected by Card Trade Guarantee`
                        })]
                    })]
                })]
            })]
        })
    }), (0,
    $.jsx)(`div`, {
        className: `absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-[#050D1A] to-transparent`
    })]
})
  , vn = [{
    icon: `ri-lock-2-line`,
    title: `Payments Held Until Confirmed`,
    description: `Your payment is secured and only released once delivery is confirmed. No money changes hands until both sides are satisfied.`,
    tag: `Escrow Protection`
}, {
    icon: `ri-shield-user-line`,
    title: `Verified Identities on Both Sides`,
    description: `Every buyer and seller goes through identity verification. Scammers can't slip through or create cloned accounts to trick you.`,
    tag: `Identity Verified`
}, {
    icon: `ri-truck-line`,
    title: `Shipping Coverage`,
    description: `Every deal includes shipping protection. If something gets lost or damaged in transit, you're covered automatically.`,
    tag: `Shipping Covered`
}, {
    icon: `ri-refund-2-line`,
    title: `Scam Reimbursement`,
    description: `If anything goes wrong, you're covered. Card Trade's built-in scam protection reimbursement means you never lose out on a bad deal.`,
    tag: `Money-Back Guarantee`
}]
  , yn = () => (0,
$.jsxs)(`section`, {
    className: `relative bg-[#050D1A] py-24 md:py-32 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute top-0 right-0 w-96 h-96 bg-[radial-gradient(ellipse_at_right,rgba(27,58,107,0.25),transparent_70%)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute bottom-0 left-0 w-80 h-80 bg-[radial-gradient(ellipse_at_left,rgba(0,200,232,0.06),transparent_70%)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-10`,
        style: {
            backgroundImage: `radial-gradient(circle, rgba(0,200,232,0.4) 1px, transparent 1px)`,
            backgroundSize: `40px 40px`
        }
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `flex flex-col lg:flex-row items-start gap-10 lg:gap-20 mb-16 md:mb-20`,
            children: [(0,
            $.jsxs)(`div`, {
                className: `lg:w-80 flex-shrink-0`,
                children: [(0,
                $.jsxs)(`div`, {
                    className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/20 rounded-full px-4 py-1.5 mb-5`,
                    children: [(0,
                    $.jsx)(`i`, {
                        className: `ri-shield-check-fill text-[#00C8E8] text-xs`
                    }), (0,
                    $.jsx)(`span`, {
                        className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                        children: `Guaranteed`
                    })]
                }), (0,
                $.jsxs)(`h2`, {
                    className: `text-3xl md:text-5xl font-extrabold text-white leading-tight`,
                    children: [`Scam Protection`, (0,
                    $.jsx)(`span`, {
                        className: `block text-transparent bg-clip-text mt-1`,
                        style: {
                            backgroundImage: `linear-gradient(135deg, #00C8E8 0%, #00D4A8 100%)`
                        },
                        children: `Guarantee`
                    })]
                })]
            }), (0,
            $.jsxs)(`div`, {
                className: `flex-1`,
                children: [(0,
                $.jsx)(`p`, {
                    className: `text-gray-300 text-base md:text-lg leading-relaxed mb-4`,
                    children: `Run the deal through Card Trade and you're protected.`
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-400 text-base leading-relaxed`,
                    children: `Payments can be secured until delivery is confirmed, and if anything goes wrong, you're covered. Every deal includes scam protection, shipping coverage, and verified identities on both sides, so scammers can't slip through or create cloned accounts.`
                }), (0,
                $.jsxs)(`a`, {
                    href: `#`,
                    className: `inline-flex items-center gap-2 mt-6 bg-[#00C8E8] text-[#050D1A] font-bold text-sm px-6 py-3 rounded-full cursor-pointer whitespace-nowrap`,
                    style: {
                        boxShadow: `0 0 24px rgba(0,200,232,0.3)`
                    },
                    children: [(0,
                    $.jsx)(`i`, {
                        className: `ri-shield-check-line`
                    }), `Start Safe Trade`]
                })]
            })]
        }), (0,
        $.jsx)(`div`, {
            className: `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6`,
            children: vn.map(e => (0,
            $.jsxs)(`div`, {
                className: `relative bg-white/[0.03] backdrop-blur-sm border border-white/[0.07] rounded-2xl p-6 overflow-hidden`,
                children: [(0,
                $.jsx)(`div`, {
                    className: `absolute top-0 right-0 w-20 h-20 bg-[radial-gradient(ellipse_at_top_right,rgba(0,200,232,0.08),transparent_70%)]`
                }), (0,
                $.jsx)(`div`, {
                    className: `absolute top-0 right-0 w-10 h-px bg-gradient-to-l from-[#00C8E8]/40 to-transparent`
                }), (0,
                $.jsx)(`div`, {
                    className: `absolute top-0 right-0 w-px h-10 bg-gradient-to-b from-[#00C8E8]/40 to-transparent`
                }), (0,
                $.jsx)(`div`, {
                    className: `w-12 h-12 flex items-center justify-center rounded-xl bg-[#00C8E8]/10 border border-[#00C8E8]/20 mb-5`,
                    children: (0,
                    $.jsx)(`i`, {
                        className: `${e.icon} text-[#00C8E8] text-xl`
                    })
                }), (0,
                $.jsx)(`span`, {
                    className: `inline-block text-[10px] font-bold text-[#00C8E8]/80 tracking-widest uppercase mb-3 bg-[#00C8E8]/10 px-2 py-0.5 rounded-full`,
                    children: e.tag
                }), (0,
                $.jsx)(`h3`, {
                    className: `text-white font-bold text-base mb-3`,
                    children: e.title
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-400 text-sm leading-relaxed`,
                    children: e.description
                }), (0,
                $.jsx)(`div`, {
                    className: `absolute bottom-0 left-6 right-6 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/20 to-transparent`
                })]
            }, e.title))
        }), (0,
        $.jsx)(`div`, {
            className: `mt-14 rounded-2xl overflow-hidden border border-[#00C8E8]/15 relative bg-[#0D1528]/60`,
            children: (0,
            $.jsxs)(`div`, {
                className: `relative w-full h-48 md:h-56`,
                children: [(0,
                $.jsx)(`img`, {
                    src: `https://readdy.ai/api/search-image?query=futuristic%20digital%20security%20shield%20protection%20concept%20holographic%20glowing%20shield%20barrier%20technology%20visualization%20dark%20background%20with%20teal%20cyan%20glow%20rays%20ultra%20wide%20panoramic%20banner&width=1280&height=224&seq=scam-banner&orientation=landscape`,
                    alt: `Scam protection coverage`,
                    className: `w-full h-full object-cover object-top`
                }), (0,
                $.jsx)(`div`, {
                    className: `absolute inset-0 bg-gradient-to-r from-[#050D1A]/95 via-[#050D1A]/50 to-[#050D1A]/95`
                }), (0,
                $.jsxs)(`div`, {
                    className: `absolute inset-0 flex flex-col items-center justify-center text-center px-6`,
                    children: [(0,
                    $.jsxs)(`div`, {
                        className: `flex items-center gap-2 mb-3`,
                        children: [(0,
                        $.jsx)(`i`, {
                            className: `ri-shield-check-fill text-[#00C8E8] text-xl`
                        }), (0,
                        $.jsx)(`span`, {
                            className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                            children: `100% Covered`
                        })]
                    }), (0,
                    $.jsx)(`h3`, {
                        className: `text-white text-2xl md:text-3xl font-extrabold max-w-lg`,
                        children: `Every Deal. Every Time. Guaranteed.`
                    }), (0,
                    $.jsx)(`p`, {
                        className: `text-gray-400 text-sm mt-2 max-w-md`,
                        children: `Card Trade's protection kicks in automatically — no forms, no fine print, no stress.`
                    })]
                })]
            })
        })]
    })]
})
  , bn = [{
    number: `01`,
    title: `Create Your Account`,
    description: `Sign up in seconds. Verify your identity with our streamlined KYC process and gain instant access to the full CardTrade marketplace, vault services, and analytics suite.`,
    icon: `ri-user-add-line`,
    image: `https://readdy.ai/api/search-image?query=futuristic%20digital%20identity%20verification%20interface%20holographic%20user%20profile%20setup%20modern%20dark%20UI%20screen%20with%20cyan%20glowing%20elements%20clean%20geometric%20design%20technology%20visualization&width=480&height=360&seq=step-1&orientation=landscape`
}, {
    number: `02`,
    title: `List or Browse Cards`,
    description: `Upload your cards with high-resolution photos and our AI will auto-suggest grades, pricing benchmarks, and comparable sales. Or explore thousands of authenticated listings from verified sellers.`,
    icon: `ri-search-2-line`,
    image: `https://readdy.ai/api/search-image?query=sleek%20futuristic%20card%20catalog%20grid%20interface%20showing%20trading%20card%20listings%20holographic%20display%20panels%20dark%20background%20with%20teal%20neon%20highlights%20premium%20product%20photography%20display%20technology&width=480&height=360&seq=step-2&orientation=landscape`
}, {
    number: `03`,
    title: `Trade with Confidence`,
    description: `Our smart escrow system holds funds securely during every transaction. Real-time verification ensures authenticity before any payment is released — protecting both buyers and sellers.`,
    icon: `ri-secure-payment-line`,
    image: `https://readdy.ai/api/search-image?query=futuristic%20secure%20digital%20payment%20escrow%20transaction%20visualization%20holographic%20blockchain%20network%20nodes%20dark%20background%20with%20cyan%20glow%20technology%20financial%20security%20concept&width=480&height=360&seq=step-3&orientation=landscape`
}, {
    number: `04`,
    title: `Grow Your Portfolio`,
    description: `Track your collection's market value in real-time. Access historical price data, trend forecasting, and personalized insights to make smarter buying and selling decisions over time.`,
    icon: `ri-pie-chart-2-line`,
    image: `https://readdy.ai/api/search-image?query=advanced%20portfolio%20analytics%20dashboard%20holographic%20data%20charts%20trading%20card%20collection%20value%20tracking%20futuristic%20dark%20interface%20with%20glowing%20cyan%20teal%20graphs%20and%20statistics&width=480&height=360&seq=step-4&orientation=landscape`
}]
  , xn = () => (0,
$.jsxs)(`section`, {
    className: `relative bg-[#07101F] py-24 md:py-32 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-[0.06]`,
        style: {
            backgroundImage: `linear-gradient(rgba(0,200,232,0.5) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0,200,232,0.5) 1px, transparent 1px)`,
            backgroundSize: `80px 80px`
        }
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 bg-[radial-gradient(ellipse_60%_50%_at_50%_50%,rgba(27,58,107,0.15),transparent)]`
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `text-center mb-16 md:mb-24`,
            children: [(0,
            $.jsx)(`div`, {
                className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/20 rounded-full px-4 py-1.5 mb-5`,
                children: (0,
                $.jsx)(`span`, {
                    className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                    children: `HOW IT WORKS`
                })
            }), (0,
            $.jsxs)(`h2`, {
                className: `text-3xl md:text-5xl font-extrabold text-white mb-6`,
                children: [`Trust Built Into`, (0,
                $.jsx)(`br`, {}), (0,
                $.jsx)(`span`, {
                    className: `text-transparent bg-clip-text`,
                    style: {
                        backgroundImage: `linear-gradient(90deg, #00C8E8, #00A8CC)`
                    },
                    children: `Every Deal`
                })]
            }), (0,
            $.jsx)(`p`, {
                className: `text-gray-400 text-base md:text-lg max-w-2xl mx-auto`,
                children: `Card Trade brings trust to every deal with verified identities, payments held until completion, and built in scam protection reimbursement if something goes wrong. Keep buying and selling on social, just without the risk and without the fees.`
            })]
        }), (0,
        $.jsx)(`div`, {
            className: `flex flex-col gap-16 md:gap-24`,
            children: bn.map( (e, t) => (0,
            $.jsxs)(`div`, {
                className: `flex flex-col ${t % 2 == 0 ? `lg:flex-row` : `lg:flex-row-reverse`} items-center gap-10 lg:gap-16`,
                children: [(0,
                $.jsxs)(`div`, {
                    className: `flex-1 text-center lg:text-left`,
                    children: [(0,
                    $.jsxs)(`div`, {
                        className: `inline-flex items-center gap-3 mb-6`,
                        children: [(0,
                        $.jsx)(`div`, {
                            className: `w-12 h-12 rounded-full flex items-center justify-center font-extrabold text-sm text-[#050D1A] bg-[#00C8E8]`,
                            style: {
                                boxShadow: `0 0 24px rgba(0,200,232,0.4)`
                            },
                            children: e.number
                        }), (0,
                        $.jsx)(`div`, {
                            className: `h-px w-8 bg-[#00C8E8]/40`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `w-8 h-8 flex items-center justify-center`,
                            children: (0,
                            $.jsx)(`i`, {
                                className: `${e.icon} text-[#00C8E8] text-lg`
                            })
                        })]
                    }), (0,
                    $.jsx)(`h3`, {
                        className: `text-2xl md:text-3xl font-extrabold text-white mb-4`,
                        children: e.title
                    }), (0,
                    $.jsx)(`p`, {
                        className: `text-gray-400 text-base leading-relaxed max-w-lg mx-auto lg:mx-0`,
                        children: e.description
                    }), (0,
                    $.jsxs)(`a`, {
                        href: `#`,
                        className: `inline-flex items-center gap-2 text-[#00C8E8] text-sm font-semibold mt-6 cursor-pointer whitespace-nowrap`,
                        children: [`Learn more `, (0,
                        $.jsx)(`i`, {
                            className: `ri-arrow-right-line`
                        })]
                    })]
                }), (0,
                $.jsx)(`div`, {
                    className: `flex-1 w-full max-w-lg mx-auto lg:mx-0`,
                    children: (0,
                    $.jsxs)(`div`, {
                        className: `relative rounded-2xl overflow-hidden border border-[#00C8E8]/15`,
                        style: {
                            boxShadow: `0 20px 60px rgba(0,0,0,0.5)`
                        },
                        children: [(0,
                        $.jsx)(`img`, {
                            src: e.image,
                            alt: e.title,
                            className: `w-full h-56 md:h-64 object-cover object-top`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute inset-0 bg-gradient-to-t from-[#07101F]/70 to-transparent`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute top-3 left-3 w-6 h-6 border-l-2 border-t-2 border-[#00C8E8]/50 rounded-tl-lg`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute top-3 right-3 w-6 h-6 border-r-2 border-t-2 border-[#00C8E8]/50 rounded-tr-lg`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute bottom-3 left-3 w-6 h-6 border-l-2 border-b-2 border-[#00C8E8]/50 rounded-bl-lg`
                        }), (0,
                        $.jsx)(`div`, {
                            className: `absolute bottom-3 right-3 w-6 h-6 border-r-2 border-b-2 border-[#00C8E8]/50 rounded-br-lg`
                        })]
                    })
                })]
            }, e.number))
        })]
    })]
})
  , Sn = [{
    name: `Charizard Base Set`,
    set: `Pokémon 1st Edition`,
    grade: `PSA 10`,
    price: `$28,500`,
    change: `+8.3%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Charizard%20Pok%C3%A9mon%20holographic%20rare%20trading%20card%201st%20edition%20base%20set%20premium%20collectible%20with%20rainbow%20holographic%20foil%20dark%20studio%20background%20product%20photography%20ultra%20high%20detail&width=240&height=336&seq=card-1&orientation=portrait`
}, {
    name: `Michael Jordan Rookie`,
    set: `1986 Fleer Basketball`,
    grade: `BGS 9.5`,
    price: `$14,200`,
    change: `+5.1%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Michael%20Jordan%20rookie%20card%201986%20Fleer%20basketball%20trading%20card%20premium%20collectible%20holographic%20foil%20dark%20studio%20background%20product%20photography%20ultra%20high%20quality%20vintage%20sports%20card&width=240&height=336&seq=card-2&orientation=portrait`
}, {
    name: `Black Lotus Alpha`,
    set: `Magic The Gathering`,
    grade: `CGC 9`,
    price: `$52,000`,
    change: `+2.7%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Magic%20The%20Gathering%20Black%20Lotus%20Alpha%20edition%20ultra%20rare%20trading%20card%20dark%20background%20holographic%20effects%20premium%20collectible%20card%20photography%20cinematic%20lighting%20dramatic%20product%20shot&width=240&height=336&seq=card-3&orientation=portrait`
}, {
    name: `Pikachu Illustrator`,
    set: `Pokémon CoroCoro`,
    grade: `PSA 9`,
    price: `$375,000`,
    change: `+15.2%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Pikachu%20Illustrator%20Pok%C3%A9mon%20promo%20card%20ultra%20rare%20holographic%20CoroCoro%20magazine%20promo%20dark%20background%20with%20dramatic%20cyan%20glow%20premium%20collectible%20card%20photography%20studio%20shot&width=240&height=336&seq=card-4&orientation=portrait`
}, {
    name: `Wayne Gretzky Young Guns`,
    set: `1979 O-Pee-Chee`,
    grade: `PSA 8`,
    price: `$9,800`,
    change: `-1.2%`,
    positive: !1,
    image: `https://readdy.ai/api/search-image?query=Wayne%20Gretzky%20ice%20hockey%20trading%20card%20vintage%201979%20collectible%20sports%20card%20premium%20product%20photography%20dark%20background%20with%20teal%20glow%20high%20contrast%20studio%20lighting%20collector%20item&width=240&height=336&seq=card-5&orientation=portrait`
}, {
    name: `LeBron James SP RC`,
    set: `2003 Upper Deck`,
    grade: `PSA 10`,
    price: `$18,600`,
    change: `+6.9%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=LeBron%20James%20rookie%20card%202003%20Upper%20Deck%20basketball%20rare%20specimen%20holographic%20foil%20dark%20studio%20background%20high%20definition%20product%20photography%20premium%20collectible%20sports%20card&width=240&height=336&seq=card-6&orientation=portrait`
}, {
    name: `Mew No. 151 Promo`,
    set: `Pokémon Promo`,
    grade: `PSA 10`,
    price: `$6,400`,
    change: `+11.8%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Mew%20Pok%C3%A9mon%20promo%20card%20number%20151%20ultra%20rare%20holographic%20foil%20dark%20background%20with%20pink%20and%20cyan%20glow%20effects%20premium%20collectible%20card%20photography%20ultra%20high%20detail%20studio%20shot&width=240&height=336&seq=card-7&orientation=portrait`
}, {
    name: `Tom Brady Rookie Auto`,
    set: `2000 Playoff Contenders`,
    grade: `BGS 10`,
    price: `$42,000`,
    change: `+3.4%`,
    positive: !0,
    image: `https://readdy.ai/api/search-image?query=Tom%20Brady%20rookie%20autograph%20football%20trading%20card%202000%20Playoff%20Contenders%20premium%20signed%20collectible%20dark%20background%20with%20teal%20neon%20glow%20premium%20sports%20card%20product%20photography%20ultra%20high%20definition&width=240&height=336&seq=card-8&orientation=portrait`
}]
  , Cn = () => (0,
$.jsxs)(`section`, {
    className: `relative bg-[#050D1A] py-24 md:py-32 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute inset-0 bg-[radial-gradient(ellipse_80%_60%_at_50%_50%,rgba(27,58,107,0.2),transparent)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-[0.04]`,
        style: {
            backgroundImage: `radial-gradient(circle, rgba(0,200,232,0.8) 1px, transparent 1px)`,
            backgroundSize: `32px 32px`
        }
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `flex flex-col md:flex-row items-start md:items-end justify-between gap-6 mb-12 md:mb-16`,
            children: [(0,
            $.jsxs)(`div`, {
                children: [(0,
                $.jsx)(`div`, {
                    className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/20 rounded-full px-4 py-1.5 mb-5`,
                    children: (0,
                    $.jsx)(`span`, {
                        className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                        children: `Live Marketplace`
                    })
                }), (0,
                $.jsxs)(`h2`, {
                    className: `text-3xl md:text-5xl font-extrabold text-white`,
                    children: [`Featured Cards`, (0,
                    $.jsx)(`br`, {}), (0,
                    $.jsx)(`span`, {
                        className: `text-transparent bg-clip-text`,
                        style: {
                            backgroundImage: `linear-gradient(90deg, #00C8E8, #00A8CC)`
                        },
                        children: `Trading Now`
                    })]
                })]
            }), (0,
            $.jsxs)(`a`, {
                href: `#`,
                className: `flex items-center gap-2 border border-[#00C8E8]/30 text-[#00C8E8] text-sm font-semibold px-5 py-2.5 rounded-full cursor-pointer whitespace-nowrap`,
                children: [`Browse All `, (0,
                $.jsx)(`i`, {
                    className: `ri-arrow-right-line`
                })]
            })]
        }), (0,
        $.jsx)(`div`, {
            className: `flex items-center gap-2 flex-wrap mb-10`,
            children: [`All`, `Pokémon`, `Sports`, `MTG`, `Hot Deals`, `PSA 10`].map( (e, t) => (0,
            $.jsx)(`button`, {
                className: `text-xs font-semibold px-4 py-1.5 rounded-full cursor-pointer whitespace-nowrap transition-colors ${t === 0 ? `bg-[#00C8E8] text-[#050D1A]` : `bg-white/5 border border-white/10 text-gray-400 hover:text-white hover:border-[#00C8E8]/30`}`,
                children: e
            }, e))
        }), (0,
        $.jsx)(`div`, {
            className: `grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4 md:gap-6`,
            children: Sn.map(e => (0,
            $.jsxs)(`div`, {
                className: `relative bg-[#0D1528]/80 backdrop-blur-sm border border-white/[0.07] rounded-2xl overflow-hidden cursor-pointer group`,
                style: {
                    boxShadow: `0 8px 32px rgba(0,0,0,0.4)`
                },
                children: [(0,
                $.jsxs)(`div`, {
                    className: `relative aspect-[3/4] overflow-hidden`,
                    children: [(0,
                    $.jsx)(`img`, {
                        src: e.image,
                        alt: e.name,
                        className: `w-full h-full object-cover object-top`
                    }), (0,
                    $.jsx)(`div`, {
                        className: `absolute inset-0 bg-gradient-to-br from-[#00C8E8]/05 via-transparent to-[#1B3A6B]/10`
                    }), (0,
                    $.jsx)(`div`, {
                        className: `absolute top-2.5 left-2.5 bg-[#050D1A]/80 backdrop-blur-sm border border-[#00C8E8]/30 rounded-full px-2 py-0.5`,
                        children: (0,
                        $.jsx)(`span`, {
                            className: `text-[#00C8E8] text-[10px] font-bold`,
                            children: e.grade
                        })
                    })]
                }), (0,
                $.jsxs)(`div`, {
                    className: `p-3 md:p-4`,
                    children: [(0,
                    $.jsx)(`p`, {
                        className: `text-[10px] text-gray-500 font-medium mb-0.5`,
                        children: e.set
                    }), (0,
                    $.jsx)(`h4`, {
                        className: `text-white text-xs md:text-sm font-bold leading-tight mb-2`,
                        children: e.name
                    }), (0,
                    $.jsxs)(`div`, {
                        className: `flex items-center justify-between`,
                        children: [(0,
                        $.jsx)(`span`, {
                            className: `text-[#00C8E8] text-sm md:text-base font-extrabold`,
                            children: e.price
                        }), (0,
                        $.jsx)(`span`, {
                            className: `text-[10px] font-bold px-1.5 py-0.5 rounded-full ${e.positive ? `bg-green-500/15 text-green-400` : `bg-red-500/15 text-red-400`}`,
                            children: e.change
                        })]
                    }), (0,
                    $.jsx)(`button`, {
                        className: `w-full mt-3 bg-[#00C8E8]/10 border border-[#00C8E8]/25 text-[#00C8E8] text-xs font-semibold py-1.5 rounded-lg cursor-pointer whitespace-nowrap`,
                        children: `View Listing`
                    })]
                })]
            }, e.name))
        }), (0,
        $.jsxs)(`div`, {
            className: `text-center mt-12`,
            children: [(0,
            $.jsx)(`p`, {
                className: `text-gray-400 text-sm mb-4`,
                children: `Over 5 million authenticated cards available right now`
            }), (0,
            $.jsxs)(`a`, {
                href: `#`,
                className: `inline-flex items-center gap-2 bg-[#00C8E8] text-[#050D1A] font-bold text-sm px-8 py-3.5 rounded-full cursor-pointer whitespace-nowrap`,
                style: {
                    boxShadow: `0 0 24px rgba(0,200,232,0.3)`
                },
                children: [`Explore Full Marketplace `, (0,
                $.jsx)(`i`, {
                    className: `ri-arrow-right-line`
                })]
            })]
        })]
    })]
})
  , wn = [{
    value: `250K+`,
    label: `Active Traders`,
    icon: `ri-group-line`
}, {
    value: `5M+`,
    label: `Cards Listed`,
    icon: `ri-stack-line`
}, {
    value: `$120M+`,
    label: `Total Volume Traded`,
    icon: `ri-exchange-dollar-line`
}, {
    value: `99.8%`,
    label: `Authentication Accuracy`,
    icon: `ri-shield-check-line`
}]
  , Tn = [{
    quote: `CardTrade completely changed how I manage my collection. The AI grading tool alone saves me hours every week and the market data is incredibly accurate. I've sold over 300 cards and every transaction was smooth.`,
    name: `Marcus J.`,
    title: `Professional Card Investor`,
    avatar: `https://readdy.ai/api/search-image?query=professional%20man%20portrait%20headshot%20confident%20collector%20investor%20dark%20background%20studio%20photography%20high%20quality%20realistic&width=64&height=64&seq=avatar-1&orientation=squarish`,
    rating: 5
}, {
    quote: `I was skeptical at first, but the vault storage service gives me total peace of mind. My BGS 10 Charizard is insured and secure, and I can list it for sale instantly whenever I want. Absolutely incredible platform.`,
    name: `Samantha R.`,
    title: `Rare Pokémon Collector`,
    avatar: `https://readdy.ai/api/search-image?query=professional%20woman%20portrait%20headshot%20confident%20collector%20dark%20background%20studio%20photography%20high%20quality%20realistic&width=64&height=64&seq=avatar-2&orientation=squarish`,
    rating: 5
}, {
    quote: `The real-time analytics are on another level. I can see exactly how my portfolio is performing versus the broader market. CardTrade has turned my hobby into a serious investment strategy.`,
    name: `Tyler W.`,
    title: `Sports Card Portfolio Manager`,
    avatar: `https://readdy.ai/api/search-image?query=young%20professional%20man%20portrait%20headshot%20smiling%20trader%20investor%20dark%20background%20studio%20photography%20high%20quality%20realistic&width=64&height=64&seq=avatar-3&orientation=squarish`,
    rating: 5
}]
  , En = [{
    name: `PSA`,
    icon: `ri-award-line`
}, {
    name: `BGS Beckett`,
    icon: `ri-medal-line`
}, {
    name: `CGC`,
    icon: `ri-verified-badge-line`
}, {
    name: `SGC`,
    icon: `ri-shield-star-line`
}, {
    name: `ACE`,
    icon: `ri-trophy-line`
}]
  , Dn = () => (0,
$.jsxs)(`section`, {
    className: `relative bg-[#07101F] py-24 md:py-32 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/15 to-transparent`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-[0.05]`,
        style: {
            backgroundImage: `linear-gradient(rgba(0,200,232,0.6) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0,200,232,0.6) 1px, transparent 1px)`,
            backgroundSize: `100px 100px`
        }
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `text-center mb-16`,
            children: [(0,
            $.jsx)(`div`, {
                className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/20 rounded-full px-4 py-1.5 mb-5`,
                children: (0,
                $.jsx)(`span`, {
                    className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                    children: `Trusted Worldwide`
                })
            }), (0,
            $.jsx)(`h2`, {
                className: `text-3xl md:text-5xl font-extrabold text-white`,
                children: `Collectors Trust CardTrade`
            })]
        }), (0,
        $.jsx)(`div`, {
            className: `grid grid-cols-2 lg:grid-cols-4 gap-4 md:gap-6 mb-20`,
            children: wn.map(e => (0,
            $.jsxs)(`div`, {
                className: `bg-white/[0.03] border border-white/[0.07] rounded-2xl p-5 md:p-6 text-center relative overflow-hidden`,
                children: [(0,
                $.jsx)(`div`, {
                    className: `absolute top-0 inset-x-0 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/25 to-transparent`
                }), (0,
                $.jsx)(`div`, {
                    className: `w-10 h-10 flex items-center justify-center rounded-xl bg-[#00C8E8]/10 border border-[#00C8E8]/20 mx-auto mb-4`,
                    children: (0,
                    $.jsx)(`i`, {
                        className: `${e.icon} text-[#00C8E8] text-lg`
                    })
                }), (0,
                $.jsx)(`div`, {
                    className: `text-3xl md:text-4xl font-extrabold text-transparent bg-clip-text mb-1`,
                    style: {
                        backgroundImage: `linear-gradient(135deg, #00C8E8, #0099B8)`
                    },
                    children: e.value
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-400 text-sm`,
                    children: e.label
                })]
            }, e.label))
        }), (0,
        $.jsx)(`div`, {
            className: `grid grid-cols-1 md:grid-cols-3 gap-6 mb-20`,
            children: Tn.map(e => (0,
            $.jsxs)(`div`, {
                className: `bg-white/[0.03] border border-white/[0.07] rounded-2xl p-6 relative overflow-hidden`,
                children: [(0,
                $.jsx)(`div`, {
                    className: `absolute top-0 right-0 w-24 h-24 bg-[radial-gradient(ellipse_at_top_right,rgba(0,200,232,0.06),transparent)]`
                }), (0,
                $.jsx)(`div`, {
                    className: `flex gap-0.5 mb-4`,
                    children: Array.from({
                        length: e.rating
                    }).map( (e, t) => (0,
                    $.jsx)(`i`, {
                        className: `ri-star-fill text-amber-400 text-sm`
                    }, t))
                }), (0,
                $.jsxs)(`p`, {
                    className: `text-gray-300 text-sm leading-relaxed mb-6`,
                    children: [`“`, e.quote, `”`]
                }), (0,
                $.jsxs)(`div`, {
                    className: `flex items-center gap-3`,
                    children: [(0,
                    $.jsx)(`div`, {
                        className: `w-10 h-10 rounded-full overflow-hidden border border-[#00C8E8]/25 flex-shrink-0`,
                        children: (0,
                        $.jsx)(`img`, {
                            src: e.avatar,
                            alt: e.name,
                            className: `w-full h-full object-cover`
                        })
                    }), (0,
                    $.jsxs)(`div`, {
                        children: [(0,
                        $.jsx)(`div`, {
                            className: `text-white text-sm font-bold`,
                            children: e.name
                        }), (0,
                        $.jsx)(`div`, {
                            className: `text-gray-500 text-xs`,
                            children: e.title
                        })]
                    })]
                })]
            }, e.name))
        }), (0,
        $.jsxs)(`div`, {
            className: `text-center`,
            children: [(0,
            $.jsx)(`p`, {
                className: `text-gray-500 text-xs font-semibold tracking-widest uppercase mb-8`,
                children: `Certified by Industry's Top Grading Authorities`
            }), (0,
            $.jsx)(`div`, {
                className: `flex items-center justify-center flex-wrap gap-6 md:gap-10`,
                children: En.map(e => (0,
                $.jsxs)(`div`, {
                    className: `flex items-center gap-2 text-gray-500 opacity-50`,
                    children: [(0,
                    $.jsx)(`div`, {
                        className: `w-6 h-6 flex items-center justify-center`,
                        children: (0,
                        $.jsx)(`i`, {
                            className: `${e.icon} text-base`
                        })
                    }), (0,
                    $.jsx)(`span`, {
                        className: `text-sm font-bold tracking-wide uppercase`,
                        children: e.name
                    })]
                }, e.name))
            })]
        })]
    })]
})
  , On = () => (0,
$.jsxs)(`section`, {
    className: `relative bg-[#050D1A] py-24 md:py-32 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute inset-0 bg-[radial-gradient(ellipse_70%_60%_at_50%_50%,rgba(0,200,232,0.08),transparent)]`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute inset-0 opacity-[0.07]`,
        style: {
            backgroundImage: `linear-gradient(rgba(0,200,232,0.4) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0,200,232,0.4) 1px, transparent 1px)`,
            backgroundSize: `50px 50px`
        }
    }), (0,
    $.jsx)(`div`, {
        className: `absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] border border-[#00C8E8]/06 rounded-full`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[400px] h-[400px] border border-[#00C8E8]/06 rounded-full`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[200px] h-[200px] border border-[#00C8E8]/08 rounded-full`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute left-0 top-1/2 -translate-y-1/2 w-64 h-80 rounded-2xl overflow-hidden opacity-10 -rotate-12 -translate-x-20`,
        children: (0,
        $.jsx)(`img`, {
            src: `https://readdy.ai/api/search-image?query=holographic%20trading%20card%20rare%20collectible%20dark%20background%20with%20subtle%20cyan%20glow%20blurred%20background%20element&width=256&height=320&seq=cta-bg-1&orientation=portrait`,
            alt: ``,
            className: `w-full h-full object-cover`
        })
    }), (0,
    $.jsx)(`div`, {
        className: `absolute right-0 top-1/2 -translate-y-1/2 w-64 h-80 rounded-2xl overflow-hidden opacity-10 rotate-12 translate-x-20`,
        children: (0,
        $.jsx)(`img`, {
            src: `https://readdy.ai/api/search-image?query=premium%20sports%20trading%20card%20rare%20collectible%20dark%20background%20with%20subtle%20blue%20glow%20blurred%20background%20decoration%20element&width=256&height=320&seq=cta-bg-2&orientation=portrait`,
            alt: ``,
            className: `w-full h-full object-cover`
        })
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-4xl mx-auto px-6 md:px-10 text-center`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `inline-flex items-center gap-2 bg-[#00C8E8]/10 border border-[#00C8E8]/25 rounded-full px-4 py-1.5 mb-7`,
            children: [(0,
            $.jsx)(`span`, {
                className: `w-1.5 h-1.5 rounded-full bg-green-400 inline-block`
            }), (0,
            $.jsx)(`span`, {
                className: `text-[#00C8E8] text-xs font-semibold tracking-widest uppercase`,
                children: `Join 250,000+ Traders`
            })]
        }), (0,
        $.jsxs)(`h2`, {
            className: `text-4xl md:text-6xl lg:text-7xl font-extrabold text-white mb-6 leading-tight`,
            children: [`Your Collection.`, (0,
            $.jsx)(`br`, {}), (0,
            $.jsx)(`span`, {
                className: `text-transparent bg-clip-text`,
                style: {
                    backgroundImage: `linear-gradient(135deg, #00C8E8 0%, #00A8CC 50%, #0099B8 100%)`
                },
                children: `Your Market.`
            })]
        }), (0,
        $.jsx)(`p`, {
            className: `text-gray-400 text-base md:text-xl max-w-2xl mx-auto mb-10 leading-relaxed`,
            children: `Start trading the world's most valuable cards today. Free to join. No listing fees on your first 50 cards. Trusted by collectors and investors globally.`
        }), (0,
        $.jsxs)(`div`, {
            className: `flex flex-col sm:flex-row items-center justify-center gap-4 mb-12`,
            children: [(0,
            $.jsx)(`a`, {
                href: `#`,
                className: `w-full sm:w-auto bg-[#00C8E8] text-[#050D1A] font-extrabold text-base px-10 py-4 rounded-full cursor-pointer whitespace-nowrap`,
                style: {
                    boxShadow: `0 0 40px rgba(0,200,232,0.4)`
                },
                children: `Create Free Account`
            }), (0,
            $.jsx)(`a`, {
                href: `#`,
                className: `w-full sm:w-auto border border-[#00C8E8]/30 text-white font-semibold text-base px-10 py-4 rounded-full cursor-pointer whitespace-nowrap`,
                children: `Talk to Sales`
            })]
        }), (0,
        $.jsxs)(`div`, {
            className: `flex flex-wrap items-center justify-center gap-6 text-gray-500 text-xs`,
            children: [(0,
            $.jsxs)(`span`, {
                className: `flex items-center gap-1.5`,
                children: [(0,
                $.jsx)(`i`, {
                    className: `ri-shield-check-line text-[#00C8E8]`
                }), `No credit card required`]
            }), (0,
            $.jsxs)(`span`, {
                className: `flex items-center gap-1.5`,
                children: [(0,
                $.jsx)(`i`, {
                    className: `ri-lock-line text-[#00C8E8]`
                }), `Bank-grade security`]
            }), (0,
            $.jsxs)(`span`, {
                className: `flex items-center gap-1.5`,
                children: [(0,
                $.jsx)(`i`, {
                    className: `ri-time-line text-[#00C8E8]`
                }), `Setup in under 5 minutes`]
            })]
        })]
    })]
})
  , kn = {
    Product: [`Marketplace`, `Vault Storage`, `Authentication`, `Analytics`, `Pricing`],
    Company: [`About Us`, `Careers`, `Press`, `Blog`, `Contact`],
    Support: [`Help Center`, `Community`, `Status`, `Security`, `Terms of Service`]
}
  , An = [{
    icon: `ri-twitter-x-line`,
    label: `Twitter/X`
}, {
    icon: `ri-discord-line`,
    label: `Discord`
}, {
    icon: `ri-instagram-line`,
    label: `Instagram`
}, {
    icon: `ri-youtube-line`,
    label: `YouTube`
}]
  , jn = () => (0,
$.jsxs)(`footer`, {
    className: `relative bg-[#030912] border-t border-[#00C8E8]/10 overflow-hidden`,
    children: [(0,
    $.jsx)(`div`, {
        className: `absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-[#00C8E8]/15 to-transparent`
    }), (0,
    $.jsx)(`div`, {
        className: `absolute bottom-0 left-0 w-80 h-60 bg-[radial-gradient(ellipse_at_bottom_left,rgba(27,58,107,0.15),transparent)]`
    }), (0,
    $.jsxs)(`div`, {
        className: `relative z-10 max-w-7xl mx-auto px-6 md:px-10`,
        children: [(0,
        $.jsxs)(`div`, {
            className: `py-14 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-10 md:gap-12`,
            children: [(0,
            $.jsxs)(`div`, {
                className: `lg:col-span-2`,
                children: [(0,
                $.jsx)(`div`, {
                    className: `flex items-center mb-4 cursor-pointer`,
                    children: (0,
                    $.jsx)(`img`, {
                        src: `https://storage.readdy-site.link/project_files/6970c675-1c7b-4278-b8c2-58ef29f9255b/4b9d7d1d-270f-46de-a3a9-a737a8c62922_logo-transparency-01.png?v=d84c9cbf8bfd391ae42e9b405e652c8e`,
                        alt: `Logo`,
                        className: `h-10 w-auto object-contain`
                    })
                }), (0,
                $.jsx)(`p`, {
                    className: `text-gray-500 text-sm leading-relaxed max-w-xs mb-6`,
                    children: `The next-generation trading card marketplace. Authenticate, collect, and trade with confidence.`
                }), (0,
                $.jsx)(`div`, {
                    className: `flex items-center gap-3`,
                    children: An.map(e => (0,
                    $.jsx)(`a`, {
                        href: `#`,
                        "aria-label": e.label,
                        className: `w-8 h-8 flex items-center justify-center rounded-full border border-white/10 text-gray-400 hover:border-[#00C8E8]/40 hover:text-[#00C8E8] transition-colors cursor-pointer`,
                        children: (0,
                        $.jsx)(`i`, {
                            className: `${e.icon} text-sm`
                        })
                    }, e.label))
                })]
            }), Object.entries(kn).map( ([e,t]) => (0,
            $.jsxs)(`div`, {
                children: [(0,
                $.jsx)(`h5`, {
                    className: `text-[#00C8E8] text-xs font-bold tracking-widest uppercase mb-4`,
                    children: e
                }), (0,
                $.jsx)(`ul`, {
                    className: `flex flex-col gap-2.5`,
                    children: t.map(e => (0,
                    $.jsx)(`li`, {
                        children: (0,
                        $.jsx)(`a`, {
                            href: `#`,
                            className: `text-gray-500 hover:text-gray-200 transition-colors text-sm cursor-pointer`,
                            children: e
                        })
                    }, e))
                })]
            }, e))]
        }), (0,
        $.jsxs)(`div`, {
            className: `border-t border-white/[0.06] py-5 flex flex-col sm:flex-row items-center justify-between gap-3`,
            children: [(0,
            $.jsxs)(`p`, {
                className: `text-gray-600 text-xs`,
                children: [`© `, new Date().getFullYear(), ` CardTrade Inc. All rights reserved.`]
            }), (0,
            $.jsx)(`div`, {
                className: `flex items-center gap-5`,
                children: [`Privacy Policy`, `Terms of Service`, `Cookie Policy`].map(e => (0,
                $.jsx)(`a`, {
                    href: `#`,
                    className: `text-gray-600 hover:text-gray-400 text-xs transition-colors cursor-pointer whitespace-nowrap`,
                    rel: `nofollow`,
                    children: e
                }, e))
            })]
        })]
    })]
})
  , Mn = () => (0,
$.jsxs)(`div`, {
    className: `min-h-screen bg-[#050D1A] font-sans`,
    children: [(0,
    $.jsx)(hn, {}), (0,
    $.jsxs)(`main`, {
        children: [(0,
        $.jsx)(`section`, {
            id: `hero`,
            children: (0,
            $.jsx)(_n, {})
        }), (0,
        $.jsx)(`section`, {
            id: `features`,
            children: (0,
            $.jsx)(yn, {})
        }), (0,
        $.jsx)(`section`, {
            id: `how-it-works`,
            children: (0,
            $.jsx)(xn, {})
        }), (0,
        $.jsx)(`section`, {
            id: `showcase`,
            children: (0,
            $.jsx)(Cn, {})
        }), (0,
        $.jsx)(`section`, {
            id: `trust`,
            children: (0,
            $.jsx)(Dn, {})
        }), (0,
        $.jsx)(`section`, {
            id: `cta`,
            children: (0,
            $.jsx)(On, {})
        })]
    }), (0,
    $.jsx)(jn, {})]
})
  , Nn = s({
    default: () => Pn
})
  , Pn = [{
    path: `/`,
    element: (0,
    $.jsx)(Mn, {})
}, {
    path: `*`,
    element: (0,
    $.jsx)(mn, {})
}];
export {qe as a, p as c, l as d, Ge as i, o as l, Pn as n, _ as o, Jt as r, h as s, Nn as t, s as u};
//# sourceMappingURL=config-BrgFsd4c.js.map
