const original = {
    date: new Date(),
    array: [1, 2, { a: 3 }],
    map: new Map([['key', 'value']]),
    set: new Set([1, 2, 3]),
    regex: /test/g,
    func: () => console.log('Hello'),
    [Symbol('id')]: 123,
    circularRef: null as any
};

original.circularRef = original;

const copy = deepClone(original);

console.log(copy); // Глубокая копия со всеми свойствами
console.log(copy !== original); // true
console.log(copy.array !== original.array); // true
console.log(copy.circularRef === copy); // true (циклическая ссылка сохранена)
