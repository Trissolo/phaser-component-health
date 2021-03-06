Phaser 3 Health Component
=========================

Flexible, data-based health component.

Examples
--------

```javascript
// Add component to *one* game object
Phaser.Health.AddTo(sprite);

// Add component and assign health 1/2
Phaser.Health.AddTo(sprite, 1, 2);

// Same:
Phaser.Health.AddTo(sprite).setMaxHealth(2).setHealth(1);

// Add component to Sprite class
Phaser.Health.MixinTo(Phaser.GameObjects.Sprite);

// Hide and deactivate sprite when health decreases below 0
sprite.on('die', function (spr) {
  spr.setActive(false).setVisible(false);
});

// Show and activate sprite when health increases above 0
sprite.on('revive', function (spr) {
  spr.setActive(true).setVisible(true);
});

// React to health changes
sprite.on('healthchange', function (spr, amount, health, maxHealth) {
  // Health changed by ${amount}, now ${health}/${maxHealth}
});
```

Tests
-----

Open [tests](./tests/) in your browser.

Static Methods
--------------

- Phaser.Health.AddTo(obj, health=1, maxHealth=100) → obj
- Phaser.Health.MixinTo(class) → class
- Phaser.Health.SetHealth(obj, health, maxHealth, silent=false) → obj

Instance Methods
----------------

- damage(amount=1, silent=false) → this
- getHealth() → amount
- getMaxHealth() → amount
- heal(amount=1, silent=false) → this
- isAlive() → boolean
- isDead() → boolean
- kill(silent=false) → this
- revive(newHealth=1, silent=false) → this
- reviveAtMaxHealth(silent=false) → this
- setHealth(health, silent=false) → this
- setMaxHealth(maxHealth, silent=false) → this

Events
------

1. `damage`, `heal` → (obj, amount)
2. `healthchange` → (obj, amount, health, maxHealth)
3. `die`, `revive` → (obj)
